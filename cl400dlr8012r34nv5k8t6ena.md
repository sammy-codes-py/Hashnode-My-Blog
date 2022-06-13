## Using Signal in Django to Delete Old Image

## Using signal to delete old profile picture when sending update request.

### What is Signal in Django.

Signals help decoupled applications get notified when actions occur elsewhere in the framework.
Signals are signals or notifications that are fired at different times

##### Examples:
- pre_save -> that is fired before a model is saved
- post_save -> witch is fired after a model is saved 
- pre_delete -> that is fired before a model is saved
- post_delete -> witch is fired after a model is saved 

We can listen to the signals and by the signal can do what we need.

#### Setting up.
After creating a Django project:

**Crating profile app**

**Terminal:**
```
python manage.py startapp profiles
```
After that, we have to add it to `INSTALLED_APPS`  in `settings.py`.

**settings.py**
```python
INSTALLED_APPS = [
.....
'profiles'
]
```
Siting up the media path in `settings.py`

**settings.py**
```python
MEDIA_URL = 'media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```

Also, we will use the Django rest framework.
Have to be installed first.

**Terminal**
```
pip install django-rest-framework
```
We have to add it to `INSTALLED_APPS`  in `settings.py`.

**settings.py**

```python
INSTALLED_APPS = [
.....
'rest-framwork',
'profiles'
]
```

To use Images we have to install `pillow`

**Terminal**
```
pip install pillow
```

Create `urls.py` in the app and include it in the core project URLs
Also, we have to set up media to `urls` so that we can access it in the browser.
**core project**
```python
from django.conf import settings
from django.conf.urls.static import static
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
# including the profiles urls
    path('api/', include('profiles.urls'))
]

# setting up media in urls
if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

```

## Now let's create a model.

In profiles app:

**models.py**
```python
class ProfileModel(models.Model):
    full_name = models.CharField(max_length=255)
    bio = models.TextField()
    profile_picture = models.ImageField(upload_to='profile_pictures', null=True, blank=True)
```
Let's run migrations

**Terminal**
```
python manage.py makemigrations
python manage.py migrate
```

Let's serializer the model.

First, create the file `serializers.py` in the profiles app.

**serializers.py**
```python
from rest_framework import serializers
from profiles.models import ProfileModel

class ProfileSerializer(serializers.ModelSerializer):
    class Meta:
        model = ProfileModel
        fields = ['id', 'full_name', 'bio', 'profile_picture']

```

## Creating Views

In the profiles app open `views.py`.

**views.py**
Will create generics API view for listing, creating, retrieving, and updating.

```python
from rest_framework.generics import ListAPIView, CreateAPIView, RetrieveAPIView, UpdateAPIView

from profiles.models import ProfileModel
from profiles.serializers import ProfileSerializer

# Listing all profiles and creating new profile
class ProfileApiViewList(ListAPIView, CreateAPIView):
    queryset = ProfileModel.objects.all()
    serializer_class = ProfileSerializer

# Retriving specific profile and updating it.
class ProfileApiViewRetrieve(RetrieveAPIView, UpdateAPIView):
    queryset = ProfileModel.objects.all()
    serializer_class = ProfileSerializer
```
And now we have to create endpoints.
In profiles app:
**urls.py**

```python
from django.urls import path
from blogTest.views import ProfileApiViewList, ProfileApiViewRetrieve

urlpatterns = [
    path('profiles/', ProfileApiViewList.as_view()),
    path('profiles/<int:pk>', ProfileApiViewRetrieve.as_view()),
]
```

Now let's run the server and go to the`http://127.0.0.1:8000/api/profiles/` endpoint.

**Terminal**
```
python manage.py runserver
```
After will open browser and navigate to `http://127.0.0.1:8000/api/profiles/` (maybe your port is different)


![Screenshot from 2022-06-04 11-42-26.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654335785295/U7lMGXsNY.png align="left")

Create a Profile:

 
![Screenshot from 2022-06-04 11-44-44.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654335928489/kAGB4snKB.png align="left")

Now we can go to that specific profile by using the `id`:

`http://127.0.0.1:8000/api/profiles/1`

![Screenshot from 2022-06-04 11-47-04.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654336055928/MO8Jc6vdP.png align="left")

Here we can send the update to the profile.
Every time when we update the profile picture, the new image will be saved in `media/profile_pictures` but let's say we don't need the old ones to be saved in the server. We will delete the old one by using the signals

## Finally let's create a signal 

In the profiles app, create a new file `signals.py`.

**signals.py**

We will use `pre_delete` -> that is fired before a model is saved

sender – Specifies a particular sender to receive signals from. See Connecting to signals sent by specific senders for more information.

```python
from django.db.models.signals import pre_save
from django.dispatch import receiver
from blogTest.models import ProfileModel

# receiver - function which will be connected to this signal
@receiver(pre_save, sender=ProfileModel) # sender - Specifies a particular sender to receive signals from.
def deleting_old_profile_pic_on_update(sender, instance, **kwargs):
    if instance.pk:
            old_profile_picture = ProfileModel.objects.get(pk=instance.pk).profile_picture
            new_profile_picture = instance.profile_picture
            if old_profile_picture and old_profile_picture.url != new_profile_picture.url:
                old_profile_picture.delete(save=False)
      
```
Then in `apps.py`  StoreConfig class, we have to overwrite the `ready` method.

**apps.py**

```python
from django.apps import AppConfig

class ProfilesConfig(AppConfig):
    default_auto_field = 'django.db.models.BigAutoField'
    name = 'profiles'

    def ready(self):
        import profiles.signals

```

And now when we update the profile picture the old one will be deleted.
