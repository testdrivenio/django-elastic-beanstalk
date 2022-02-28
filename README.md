# Deploying Django to AWS Elastic Beanstalk

Check out the [tutorial](https://testdriven.io/blog/django-elastic-beanstalk/).

## Want to use this project?

### Local setup

1. Fork/Clone

1. Create and activate a virtual environment:

    ```sh
    $ python3 -m venv venv && source venv/bin/activate
    ```

1. Install the requirements:

    ```sh
    (venv)$ pip install -r requirements.txt
    ```

1. Spin-up a PostgreSQL container:

    ```sh
    (venv)$ docker run --name django-images-postgres -p 5432:5432 \
    -e POSTGRES_USER=django-images -e POSTGRES_PASSWORD=complexpassword123 \
    -e POSTGRES_DB=django-images -d postgres
    ```

1. Apply the migrations:

    ```sh
    (venv)$ python manage.py migrate
    ```

1. Run the server:

    ```sh
    (venv)$ python manage.py runserver
    ```

1. Navigate to [http://localhost:8000/](http://localhost:8000/) in your favorite web browser.

### Elastic Beanstalk setup

1. [Install EB CLI](https://github.com/aws/aws-elastic-beanstalk-cli-setup#2-quick-start).

1. Initialize Elastic Beanstalk:

    ```sh
    $ eb init
    ```

1. Create an Elastic Beanstalk environment:

    ```sh
   $ eb create django-images-env
    ```

1. Obtain your EB CNAME by running `eb status` and add it to `ALLOWED_HOSTS` inside *core/settings.py*.

1. Configure AWS RDS, S3, and Certificate Manager

1. Commit all the changed files to git and deploy:

   ```sh
   $ git add .
   $ git commit -m "updates for eb"

   $ eb deploy
   ```

1. Open the web application in your favorite web browser:

   ```sh
   $ eb open
   ```
