# 🙊 UOP - Unpopular Opinion API

## ❓ What is UOP API
UOP it's an App where you can know how popular are your opinions based on what other people respond to the same opinions and a general overview of everything you've have thought about. And this is the API that supports it.

## 📑 Models

User
```javascript
username: String // required
email: String // required & unique
password: String // required
favorites: [ObjectID<Opinions>] // not required
followers: [ObjectID<Followers>] // not required
following: [ObjectID<Following>] // not required
location: {lat: Number, long: Number} // required
```

Opinion
```javascript
author: ObjectID<User> // required
category: Array[Enum]  // required & defined by the App
question: String // required
response: {x: String, y: String} // required
photo: String
location: {lat: Number, long: Number} // required
reported: { 
    isReported: Boolean (default: false), // user reports an opinion
    isRevised: Boolean (default: false), // admin checks the report
    by: [ObjectID<user>] // users that reported the opinion
}
```

Response 
```javascript
opinion :ObjectID<opinion> 
responses: Array[
    {
        user: ObjectID<user>,
        response: Array[enum]
    }
] 
```

## 📍 Endpoints

### Auth
|Method|Route|Functionality|
|---|---|---|
|`GET`|/auth/me|Check session status|
|`POST`|/auth/signup|Log in user to app and set user to session (Body: username, email, password)|
|`POST`|/auth/login|Register user to app and set user to session (Body: username, mail, password)|
|`POST`|/auth/logout|Log out user from app and remove session|

### Users
|Method|Route|Functionality|
|---|---|---|
|`GET`|/:id|Gives back all the information of the user|
|`PUT`|/|Updates his own information|


### Opinions
|Method|Route|Functionality|
|---|---|---|
|`GET`|/opinion|Gives back all the opinions that haven't been responded by the user|
|`POST`|/opinion|Creates a new opinion card inside the platform|
|`GET`|/opinion/all|Gives back all the opinions with author data|
|`GET`|/opinion/categories|Gives back all the available categories|
|`POST`|/opinion/response|Sends the response of the user to an opinion|

### Statistics
|Method|Route|Functionality|
|---|---|---|
|`POST`|/|Receives a query object with the required statistic config|

### Admin
|Method|Route|Functionality|
|---|---|---|
|`DELETE`|/user/:id|The admin deletes the profile of a user|
|`GET`|/reported|Gives all reported opinions unchecked|
|`PUT`|/reported|Updates Opinion and Reported as checked|
|`DELETE`|/reported/:id|Deletes an Opinion|

## 😎 Demo user
```javascript
{
  username: "demo",
  password: "demo"
}
```

## ⚓️ Links
- [UOP](https://uop.jorgedejuana.com/)
- [UOP Repo](https://github.com/JdeJ/UOP.git)

## 🎖 Contribute
Support by giving a ⭐. Any suggestions are welcome!