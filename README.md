Hello, this is my Capstone Project I took when I take the course of IBM Back-end Development in Coursera.
In this project I made a backend server for a Band Website with 2 micorservices **Get Pictures** and **Get Songs**.
This project is created with a sample database, and you can add new database on the Django Admin site.
Before you can use this back-end services, you need to install the requirements first.

# Lab

1. Get into the directory by `cd sfvih-Back-end-Development-Capstone`
2. Get into Django code `cd djangoserver`
3. Install requirements `pip install -r requirements.txt`
4. Create the initial migrations and generate the database schema:
    ```shell
    python manage.py makemigrations
    python manage.py migrate
    ```
5. Run the server `python manage.py runserver`
6. Launch Application
7. Click on Songs and Photos
8. Click on Concerts, no existing Concert present
9. Let's create admin user `python manage.py createsuperuser`
    1. Username: `admin`
    2. Email address: _leave blank, simply press enter_
    3. Password: Your choice, or simply `qwerty123`
10. Run the server again `python manage.py runserver` and goto admin: `http://localhost:8000/admin/`
11. Enter the admin user details you created in previous step.
12. Now you are in the admin section built by Django.
13. Add a Concert
    example:
    1. Concert name: `Coachella 2023`
    2. Duration: `72`
    3. City: `Indio, California`
    4. Date: `2023-04-14`
14. Click on `View Site` meny at the top
15. Now if you visit `Concerts`, you will see Coachella listed.
16. Our Django application is now running.

## Cleanup while testing

```shell
find . -path "*/migrations/*.py" -not -name "__init__.py" -delete
find . -path "*/migrations/*.pyc"  -delete
find . -path "*/db.sqlite3"  -delete
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```

##  To move the data from SQLite to MySQL

Execute:

`python manage.py dumpdata > datadump.json`

Next, change your `settings.py` to the mysql database.

Finally:

`python manage.py loaddata datadump.json`

##  Containerize the application
1. build a docker image
    ```
    docker build . -t concert
    ```
1. tag docker image with the correct registry information
    ```
    docker tag concert captainfedora/concert:v1
    ```
    The above command tags to `captainfedora` repository on dockerhub with the image name of `concert` and label of `v1`

1. Run the docker image to validate everything is working
    ```
    docker run -p 8000:8000 captainfedora/concert:v1
    ```
