# REST APIs with Flask, Python and SQLite Database

It has a sample implementation for GET, PUT, POST, DELETE methods, and also has a simple demonstration for JTW for the authentication. It uses SQLite for the CRUD operations. 

## some usefull commands to create this kind of project:

```
$ mkdir project-x
$ cd project-x
$ atom .
$ pip install virtualenv
$ pip freeze
$ virtualenv venv --python=python3.7 # to create virtual enviroment
$ source venv/bin/activate
$ deactivate
$ pip install Flask-RESTful # to install required packages
$ pip install Flask-JWT
$ python app.py # to run the project
```


## Sqlite database creation
run the following on the console under the root path
```
$ python create_table.py # it creates data.db database under the root path
```


## Sample Rest API Endpoints

### POST - Create new user / Register
sample input for localhost:5000/register
```
curl --location --request POST 'localhost:5000/register' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username":"rasim",
    "password": "123456"
}'
```
sample output
```
{
    "message": "User created successfully."
}
```


### GET
sample input for all items
```
localhost:5000/items
```
sample output
```
{
    "items": [
        {
            "name": "piano",
            "price": 15.99
        }
    ]
}
```

sample input for one item with JTW token
```
curl --location --request GET 'localhost:5000/item/piano' \
--header 'Authorization: JWT {-to-be-generated-with-auth-endpoint}'
```
sample output 
```
{
    "item": {
        "name": "piano",
        "price": 15.99
    }
}
```

### POST
sample input for localhost:5000/item/piano
```
curl --location --request POST 'localhost:5000/item/piano' \
--header 'Content-Type: application/json' \
--data-raw '{
    "price": 15.99
}'
```
sample output
```
{
    "name": "piano",
    "price": 15.99
}
```

### PUT
sample input
```
curl --location --request PUT 'localhost:5000/item/piano' \
--header 'Content-Type: application/json' \
--data-raw '{
    "price": 55.99
}'
```
sample output
```
{
    "name": "piano",
    "price": 55.99
}
```
### DELETE
sample input for localhost:5000/item/piano
```
curl --location --request DELETE 'localhost:5000/item/piano'
```
sample output
```
{
    "message": "item deleted"
}
```
### JWT AUTH

sample input for localhost:5000/auth
```
curl --location --request POST 'localhost:5000/auth' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username":"bob",
    "password": "123456"
}'
```
sample output
```
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1OTg4NzY2NzksImlhdCI6MTU5ODg3NjM3OSwibmJmIjoxNTk4ODc2Mzc5LCJpZGVudGl0eSI6MX0.GRbjEjyo_X8ifVs9ct4qU0ROYz1kGnPxyjwqk8NYBLw"
}
```


