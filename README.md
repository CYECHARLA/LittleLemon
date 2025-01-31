# Little Lemon Restaurant API

## Description
This project is the final assignment for the Backend Developer Capstone Course of the Meta Backend Developer Professional Certificate on Coursera.

## Project Structure
The project consists of two apps:
- `api`: Handles all API endpoints.
- `restaurant`: Serves the frontend interface.
- `config`: The main project directory that contains essential project settings.

## Installation
### Install Dependencies
```bash
pipenv install
```

### Activate Virtual Environment
```bash
pipenv shell
```

## Setup
### Database Configuration
The default database settings are:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'littlelemon',
        'HOST': 'localhost',
        'PORT': '3306',
        'USER': 'admin',
        'PASSWORD': '',
        'OPTIONS': {
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'",
        },
    },
}
```
💡 Update these settings based on your local setup.

### Apply Migrations
```bash
python manage.py migrate
```

## Environment Variables
For authenticated API requests in the restaurant app, a username and password must be provided.

### Steps:
1. Inside the `restaurant` app folder, create a file named `.env`.
2. Add the following:
```bash
USERNAME=your_username
PASSWORD=your_password
```
💡 Replace `your_username` and `your_password` with valid credentials.
💡 Ensure `django-environ` is installed by running `pipenv install`.

## API Endpoints
The `api` app exposes four primary endpoints, along with additional endpoints from `Djoser` and `SimpleJWT`.

### Authentication
Each request requires a SimpleJWT token for authorization. Include the token in the request header:
```bash
{'Authorization': 'JWT <token>'}
```


### `api` Endpoints
```bash
http://127.0.0.1:8000/api/menu-items
http://127.0.0.1:8000/api/menu-items/{menu-itemId}
http://127.0.0.1:8000/api/bookings
http://127.0.0.1:8000/api/bookings/{bookingId}
```
#### Menu Items
| Method | Action | Token Auth | Status Code |
|--------|--------|------------|-------------|
| GET | Retrieve all menu items | Yes | 200 |
| POST | Create a menu item | Yes | 201 |

#### Single Menu Item
| Method | Action | Token Auth | Status Code |
|--------|--------|------------|-------------|
| GET | Retrieve menu item details | Yes | 200 |
| PUT | Update menu item | Yes | 200 |
| PATCH | Partially update menu item | Yes | 200 |
| DELETE | Delete menu item | Yes | 200 |

#### Bookings
| Method | Action | Token Auth | Status Code |
|--------|--------|------------|-------------|
| GET | Retrieve all bookings | Yes | 200 |
| POST | Create a booking | Yes | 201 |

#### Single Booking
| Method | Action | Token Auth | Status Code |
|--------|--------|------------|-------------|
| GET | Retrieve booking details | Yes | 200 |
| PUT | Update booking | Yes | 200 |
| PATCH | Partially update booking | Yes | 200 |
| DELETE | Delete booking | Yes | 200 |

### `Djoser` Endpoints
```bash
http://127.0.0.1:8000/auth/users/
http://127.0.0.1:8000/auth/users/me/
http://127.0.0.1:8000/auth/users/confirm/
http://127.0.0.1:8000/auth/users/resend_activation/
http://127.0.0.1:8000/auth/users/set_password/
http://127.0.0.1:8000/auth/users/reset_password/
http://127.0.0.1:8000/auth/users/reset_password_confirm/
http://127.0.0.1:8000/auth/users/set_username/
http://127.0.0.1:8000/auth/users/reset_username/
http://127.0.0.1:8000/auth/users/reset_username_confirm/
```
| Method | Action | Status Code | Token Auth |
|--------|--------|-------------|------------|
| GET | Retrieve all users | 200 | No |
| POST | Create a user | 201 | No |

💡 Refer to the [Djoser documentation](https://djoser.readthedocs.io/en/latest/getting_started.html#available-endpoints) for further details.

### `SimpleJWT` Endpoints
```bash
http://127.0.0.1:8000/api/token/login/
http://127.0.0.1:8000/api/token/refresh/
```
| Method | Action | Token Auth | Status Code |
|--------|--------|------------|-------------|
| POST | Generate access and refresh tokens | Yes | 201 |
| POST | Refresh access token | Yes | 201 |

## Testing
This project includes 12 automated tests to validate API endpoints and their functionality.

### Run Tests
```bash
python manage.py test
```

### Expected Output
```bash
Found 12 test(s).
Creating test database for alias 'default'...
System check identified no issues (0 silenced).
............
----------------------------------------------------------------------
Ran 12 tests in 6.024s

OK
Destroying test database for alias 'default'...
```
💡 The tests validate `restaurant` models by creating entries in the database via Django ORM.
```

