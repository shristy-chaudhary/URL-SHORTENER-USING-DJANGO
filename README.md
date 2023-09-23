# URL-SHORTENER-USING-DJANGO
This project aims to develop a simple yet functional URL shortener application using the Django web framework. Django is a high-level Python web framework platform that allows developers to create web applications quickly and efficiently it follows MVC(Model-View-Controller) or MVT(Model-View-Template) architecture that provides an organized and scalable structure to develop the application. Django is known for its robustness, scalability, and security, making it an ideal choice for building web applications that require high performance and reliability. The URL Shortener by Django is a web application that allows users to shorten long URLs and manage them efficiently. It provides a user-friendly interface for creating and managing shortened URLs. The application also provides analytics on the usage of the shortened URLs, such as the number of clicks, the location of the clicks, and the time of the clicks. The URL Shortener by Django can be used for various purposes, such as social media marketing, affiliate marketing, and brand management. It can help businesses and individuals to promote their products and services on social media platforms and track the effectiveness of their marketing campaigns.

Methodology
step by step methodology for developing your URL shortener using Django's MVT architecture:

1. Setup the Django project

Create the Django project using django-admin startproject <projectname>. This creates the main project files and folders.
Create the Django app using django-admin startapp <appname>. I created an urlsam app for the URL shortener.
Add the app to INSTALLED_APPS in settings.py.
2. Define the data model

Create the Url model in models.py of the app. This will have the two fields - - full_url
containing the original long URL and short_url containing the shortened URL.

 class Url(models.Model):
 full_url = models.CharField(max_length=400, unique=True)
 short_url = models.CharField(max_length=20, unique=True)
Add a custom create() method to generate the short URL using MD5 hashing as MD5 generates a unique 128-bit hash value that I can use as the short URL key. MD5 ensures that even small changes to the input will produce a completely different hash, so it's suitable for generating unique short URLs.

3. Define the URL patterns

In urls.py of the app, define two URL patterns:
• An empty path '' maps to the view for creating a new URL.

          path('', creatUrl),   # Maps to view for creating new URL
• A path 'slug:key' maps to the view for redirecting to the full URL using the short URL key.

          path('<slug:key>', routeToURL)  # Maps to view for redirecting using short URL
          
 This routing structure allows simple and clean URLs for the two actions - creation and   
 redirection.
4. Create the views

In views.py,I created two views - one to create a new short URL and the other to redirect using a short URL key:

• creatUrl(): Handles the form POST request for creating a new short URL. It saves new Url object and returns the form again with the generated short URL.

                     def creatUrl():  # Handles creating new short URL    
• routeToURL(): Tries to retrieve the Url object using the key from the URL. If found,it redirects to the corresponding full URL.

                     def routeToURL(request, key): # Handles redirecting using short URL
5. Create the template

Create index.html template to display the form for entering a new URL and the generated short URL. The form action points to the '' URL pattern mapped to the view for creation”.
6. Run migrations

python manage.py makemigrations

python manage.py migrate

7. Test and debugging the app

Run the development server and test the application by generating several short URLs from different full URLs and verifying that the short URLs correctly redirected.

Debug and fix any issues arose during the development and testing.

8. Deploy the app

Setup the server and deploy the Django project.

Users can now generate short URLs from the deployed URL.

Result:
A working URL shortener application was successfully developed using Django's MVT architecture. The application performs the following functionalities:

• Allows users to enter a long URL and submit the form. The view function creatUrl() then generates a short URL using MD5 hashing and saves the Url model object with the full and short URLs.

• The index.html template displays the generated short URL to the user.

• Users can copy and share the short URL. When they access the short URL, the routeToURL() view function retrieves the corresponding Url object using the key from the URL and redirects the user to the full original URL.

![12](https://github.com/shristy-chaudhary/URL-SHORTENER-USING-DJANGO/assets/110960844/4c2ebaae-3523-470c-bffa-ae85bf61cad7)
![23](https://github.com/shristy-chaudhary/URL-SHORTENER-USING-DJANGO/assets/110960844/7455bc85-f3d5-4ec5-b833-4b7507b9622a)

Conclusion
This project presented a URL shortener service built using the Django web framework. The objectives of the project were met by:

• Developing a web application that can shorten long URLs submitted by users. The shortened URLs are stored in a database along with the original URLs.

• Keeping track of the click count for each shortened URL. The application stores the number of times each short link has been clicked.

• Allowing users to create custom shortened URLs containing their chosen text as the back half.

The URL shortener was implemented using Django and a SQLite database. Django models were used to define the URL and click count models. Django forms were created to accept long URLs from users and generate custom shortened URLs.

The project demonstrated how a simple yet useful web application can be developed using Django. The following were the key takeaways:

• Django provides many features out of the box for rapidly building web applications. The admin interface, models, forms, views, and URLs made development straightforward.

• The MVT (Model-View-Template) architecture of Django helps keep code organized and testable.

• The SQLite database was sufficient for the purposes of this project. However, Django also supports other databases like PostgreSQL.
