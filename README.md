# Django authentication boilerplate using JWT

Writing goes here

<a href = "https://github.com/itsmais/telegram-bot-github-notifications">
<img src = "./header.png"/ alt="django and jwt logos">
</a>

## Steps

This guide helps you get started with implementing JSON Web Tokens (JWT) authentication in a Django project.

**Step 1: Set Up Virtual Environment**

Create a new directory for your project and navigate to it in the terminal:

```bash
mkdir django-jwt-auth-boilerplate
cd django-jwt-auth-boilerplate
```

Create and activate a virtual environment:

```bash
python -m venv venv
source venv/bin/activate # linux
venv\Scripts\activate # windows
```

**Step 2: Install Django**

Install Django using pip within your virtual environment:

```bash
pip install django
```

**Step 3: Create a Django Project**

Create a new Django project:

```bash
django-admin startproject jwt_boilerplate
cd jwt_boilerplate
```

**Step 4: Create a Django App**

Create a new Django app within the project:

```bash
python manage.py startapp authentication
```

**Step 5: Install Required Packages**

Install the necessary packages for JWT authentication:

```bash
pip install djangorestframework djangorestframework-simplejwt
```

**Step 6: Configure Settings**

**Step 7: Configure Email provider**
In my case, I am playing with a gmail account.
To use Gmail as your EMAIL_HOST_USER and send emails automatically from your Django application, you'll need to configure your Gmail account to allow access for less secure apps or generate an App Password. Keep in mind that using less secure methods might expose your account to potential security risks, so it's recommended to use App Passwords for added security.

Here's how you can set it up:

Using App Passwords (Recommended)
https://support.google.com/mail/answer/185833?hl=en
Go to your Google Account settings: https://myaccount.google.com/security.
Under the "Signing in to Google" section, click on "App passwords."
Select the "Mail" app and the device you'll use.
Generate the app password and copy it.
In your Django project's settings.py, replace the value of EMAIL_HOST_PASSWORD with the generated app password.
Using Less Secure Apps (Not Recommended)

Go to your Google Account settings: https://myaccount.google.com/security.
Under the "Less secure app access" section, turn on "Allow less secure apps."

**Step 11: Run Migrations**

Run the initial migrations to create the necessary database tables:

```bash
python manage.py makemigrations
python manage.py migrate
```

**Step 12: Create Superuser**

Create a superuser to access the Django admin panel:

```bash
python manage.py createsuperuser
```

**Step 13: Run the Development Server**

Start the development server:

```bash
python manage.py runserver
```

## Registering an account

```
curl -X POST http://localhost:8000/api/register/ -H "Content-Type: application/json" -d '{
    "username": "new_user",
    "email": "new_user@example.com",
    "password": "secure_password"
}'

```

### Singing in

curl -X POST http://localhost:8000/api/token/ -H "Content-Type: application/json" -d '{
"username": "new_user",
"password": "secure_password"
}'

### Reset password

The below does not work because of cookies
curl -X POST http://localhost:8000/password_reset/ -d "email=user@example.com"
