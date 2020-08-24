![alt tag](https://github.com/LiusStarSpace/OnlineEducation_Python/blob/master/docs/media/logo.png)
# LiusStarSpace-online_education
## Description
A open-source platform for online course-based learning and education.


## Features
* Students log in and enroll in the provided courses
* Watch educational online videos lectures for courses
* Fill out quizzes tests and assignments to get graded on
* Earn certificates of completion of courses

## System Requirements
* Python 3.4.x+
* Postgres SQL DB 9.4+
* pip 6.1.1+
* virtualenv 12.1.1+

## Dependencies
See [requirements.txt](https://github.com/LiusStarSpace/OnlineEducation_Python/blob/master/requirements.txt) for more information.

## Build Instructions
### Application
For Linux and OSX users, run these commands:

1. First clone the project locally and then go into the directory
  ```
  $ git clone https://github.com/LiusStarSpace/OnlineEducation_Python.git 
  $ cd OnlineEducation_Python
  ```

2. Setup our virtual environment
  ```
  (OSX)
  $ python3 -m venv env

  (Linux)
  $ virtualenv env
  ```

3. Now lets activate virtual environment
  ```
  $ source env/bin/activate
  ```

4. OSX USERS ONLY: If you are using ‘Postgres.app’, you’ll need to have pg_config setup in your $PATH. If you already have set this up, skip this step, else simply run this command in the console to set the path manually.

  ```
  $ export PATH="/Applications/Postgres.app/Contents/Versions/9.4/bin:$PATH"
  ```

5. Now lets install the libraries this project depends on.
  ```
  $ pip install -r requirements.txt
  ```

### Database
We are almost done! Just follow these instructions and the database will be setup for the application to use.

1. Load up your postgres and enter the console. Then to create our database, enter:
  ```
  # # vi /etc/postgresql/xx.xx/main/postgresql.config
  # # Add remote link:
  # # listen_addresses = '127.0.0.1'
  # # vi /etc/postgresql/xx.xx/main/pg_hba.config
  # # Add:
  # # host    all             all              0.0.0.0/0              md5
  # sudo /etc/init.d/postgresql start
  # service postgresql start
  # sudo su postgres   
  # psql
  postgres=# create database online_edu_python_db;
  ```

2. To confirm it was created, run this line, you should see the database in the output
  ```
  # \l
  ```

3. Enter the database
  ```
  # \c online_edu_python_db
  ```

4. If you haven’t created an administrator for your previous projects, create one now by entering:
  ```
  postgres=# CREATE USER django WITH PASSWORD '123password';
  postgres=# GRANT ALL PRIVILEGES ON DATABASE online_edu_python_db to django;
  ```

5. Your database "online_edu_python_db" is now setup with an admin user account "django" using the passowrd "123password”. 

### Application + Database
Run the following command to create your custom settings instance. Note: Please write all your application passwords here as it won't be tracked on git.
  ```
  $ cd online_edu_python_project/online_edu_python_project
  $ cp secret_settings_example.py secret_settings.py
  ```

Run the following commands to populate the database.
  ```
  $ cd ../online_edu_python_project
  $ python manage.py makemigrations
  $ python manage.py migrate 
  $ python manage.py setup_online_edu_python
  ```

## Usage
To run the web-app, you’ll need to run the server instance and access the page from your browser. 

Start up the web-server:
  ```
  $ cd online_edu_python_project
  $ python manage.py runserver
  ```

In your web-browser, load up the following url
  ```
  http://127.0.0.1:8000/
  ```

Congratulations, you are all setup to run the web-app! Have fun coding!

## License
This web-app is licensed under the Apache 2.0 license. See [LICENSE.md](LICENSE.md) for more information.

## Developers
* Robert.LIU
* wslover

## Support
You can financially support the project by either:
![alt_tag](https://cdn.jsdelivr.net/gh/CN-Robert-LIU/images@master/blog/images/alipay_in.jpg)
