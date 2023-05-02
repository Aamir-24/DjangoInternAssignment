# DjangoInternAssignment

1. Setting up a Django project and app:
   django-admin startproject projectname
   python manage.py startapp appname

2.    Creating the models:

Models are classes that define the structure of the database tables. In this case, we need three models: Client, Artist, and Work.

The Client model has two fields: name and user. The user field is a foreign key to the built-in User model of Django. This allows us to associate a client with a user who has registered on the site.

The Artist model has two fields: name and works. The works field is a many-to-many relationship with the Work model. This allows us to associate multiple works with a single artist.

The Work model has two fields: link and work_type. The link field is a URLField that stores the link to the artist's work. The work_type field is a CharField with choices that allow us to specify the type of work. In this case, we have three choices: Youtube, Instagram, and Other.

3. Signals are a way to trigger certain actions in response to specific events in Django. In this case, we want to create a new Client object whenever a new User is         registered on the site.

We use the post_save signal to create the new Client object. We also use the receiver decorator to register the signal.

4.Creating the serializers:

Serializers are classes that convert complex data types (like Django models) into simple data types (like JSON) that can be easily transferred over the internet. In this case, we need three serializers: ClientSerializer, ArtistSerializer, and WorkSerializer.

The ClientSerializer and WorkSerializer are straightforward - they simply map the fields of the models to their corresponding JSON fields.

The ArtistSerializer is a bit more complex because it needs to include the works associated with each artist. We use the nested serializer technique to include the works.

5.Creating the views:

Views are classes that handle requests from the client and return responses. In this case, we need three views: WorkList, ArtistList, and RegisterClient.

The WorkList view retrieves all the works from the database and serializes them using the WorkSerializer. It also includes filter and search functionality using the DjangoFilterBackend and SearchFilter classes.

The ArtistList view retrieves all the artists from the database and serializes them using the ArtistSerializer. It also includes search functionality using the SearchFilter class.

The RegisterClient view creates a new Client object when a POST request is sent with the username and password in the request body.

6.Creating the URLs:

URLs are the endpoints that clients can access to interact with the API. In this case, we need three URLs: /api/works, /api/artist, and /api/register.

Each URL is mapped to a corresponding view using the path function from the django.urls module.

    Adding the app to INSTALLED_APPS:

In order to use the app, you need to add it to the INSTALLED_APPS list in the settings.py file. You also need to add the required third-party apps: rest_framework and django_filters.

    Migrating the database:

Finally, you need to migrate the database to create the tables for the models. You can do
