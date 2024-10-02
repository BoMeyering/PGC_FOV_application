# PGC_FOV_application

Start a new virtualenv (I like using pyenv) to get started.
```
$ pyenv virtualenv 3.11.8 fov
$ pyenv local fov
$ pip install -r requirements.txt 
```

To run the application, make sure you have [Docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04) and [Docker-compose](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04) installed on your system.
From the root directory run
```
$ docker compose up -d
```

You should see some output in the terminal like
```
[+] Running 3/3
 ⠿ Network pgc_fov_application_default          Created           0.1s
 ⠿ Container fov_postgres                       Started           0.2s
 ⠿ Container fov_adminer                        Started           0.4s
```

Then stand up the development server with
```
$ python manage.py runserver
```

This will allow you to hot reload any changes you make and see them at `localhost:8000/`

If you make changes to the database after migrations, or you want to refresh after you made some model migrations run the following
```
$ find . -path '*/migrations/*.py' ! -name '__init__.py' | xargs rm
```
Which will remove all of the migrations files from the fov app
