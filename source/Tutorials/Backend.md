---
layout: default
title: Backend
nav_order: 4
permalink: Tutorials/Backend
parent: Tutorials
has_toc: false
---

# Backend Web Development
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

This tutorial will provide an overview of the process of backend coding and key concepts.

### **Project Setup**

1. Create your project folder

2. Create an `app.py` file at the root level of your project folder

3. Install a Web Framework and Web Server

#### **Why a Web Framework?**
Nowadays, people don't code everything from scratch. Instead, we use frameworks as a shortcut! Frameworks help us write clean, organized code faster by providing tools and structure to form kind of a template. Because the code is much more condensed, it's also easier to read and understand.

This tutorial will showcase the FastAPI framework for Python. In the terminal:

```bash
pip install fastapi
```

And for the web server, we'll be using Uvicorn. In the terminal:

```bash
pip install uvicorn
```

Now to create an instance of your app, add the following in `app.py`:

```py
from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Welcome to the FastAPI backend!"}
```

Boom. Now you have an app. Make sure you're in the project directory, then you can run your app in the terminal like so:

```bash
uvicorn app:app --reload
```

If you visit `http://localhost:8000` you should see your message!

---

### **Routing & HTTP Methods**

Whenever you visit a webpage or send data from a form, your browser makes an HTTP request. That HTTP request will contain a URL, and sometimes a request body too in JSON format. Check out the structure of a URL in this example:

```
https://example.com/products/shoes?id=123
```

| Part             | Meaning           |
|------------------|-------------------|
| `https://`       | Protocol          |
| `example.com`    | Domain            |
| `/products/shoes`| Path              |
| `?id=123`        | Query string      |


#### **Routing**

The purpose of routing is to map the URL of each HTTP request (like `/home` or `/api/products`) to a specific function or handler on the server. With this, we can build the desired responses that will be sent from the server side to the web client.

For example, say we want to have a message for the URL `http://localhost:8000/hello` on our website. We could accomplish this with the following code:

```python
@app.get("/hello")
def say_hello():
    return {"message": "Hello, world!"}
```
Here, we use a GET request to look for the URL path `/hello` and return a JSON response with a message when found. GET is one of many HTTP methods used for handling data sent on the web.

#### **HTTP Methods (The Main Ones)**
```py
# Example data model - don't worry too much about it now, we'll go over it in the next section
class Item(BaseModel):
    name: Optional[str] = None
    price: Optional[float] = None
    description: Optional[str] = None

# GET method: retrieve data
@app.get("/items/{item_id}")
async def read_item(item_id: int):
    return {"item_id": item_id}

# POST method: create data
@app.post("/items/")
async def create_item(item: Item):
    return {"message": "Item created!", "item": item}

# PUT method: update data
@app.put("/items/{item_id}")
async def update_item(item_id: int, item: Item):
    return {"message": f"Item {item_id} updated!", "item": item}

# PATCH method: partially update data
@app.patch("/items/{item_id}")
async def patch_item(item_id: int, item: Item):
    return {
        "message": f"Item {item_id} partially updated!",
        "updated_fields": item.dict(exclude_unset=True)
    }

# DELETE method: delete data
@app.delete("/items/{item_id}")
async def delete_item(item_id: int):
    return {"message": f"Item {item_id} deleted!"}
```

Notice each line beginning with @ before the function definitions. These are route decorators, with `@app.{method}(URL)` specifying what pairing of HTTP method and URL is needed to execute the following function.

Included in some URLs, `{item_id}` denotes a path parameter, which is just a placeholder for whatever part of the path is found in the URL after `/items/`. We can pass the value in the braces to the function. `item_id: int` tells us that it should be an int type.

---

### **Request & Response Models with Pydantic**

FastAPI uses **Pydantic** models to let you define the structure of your data (the JSON in request bodies and responses) clearly. This allows for easy and automatic data validation, which is checking to make sure that the data matches a certain format and throwing an error when it doesn't. It's important to ensure the consistency of the data in requests and responses so that it can be predictably worked with, meaning less bugs.


For example, say we define the following model:
```python
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    price: float
    in_stock: bool = True
```

Then, say we create an endpoint for POST requests:
```python
@app.post("/items/")
def create_item(item: Item):
    return item
```
FastAPI will check to see if the data in the POST request body follows the format of the Item model, then it will send a JSON response also in that format. It might look something like this:
```JSON
{
  "name": "Laptop",
  "price": 999.99,
  "in_stock": true
}
```

---

### **Database Integration**

We will demonstrate MongoDB, a NoSQL database. Keep in mind that databases are essential for websites that store a lot of data that may change, although simple, static websites may not require them.

#### **MongoDB Basics**
MongoDB stores data in BSON documents (JSON but binary), with key-value pairs called fields. Groups of documents are organized into collections. Also remember that as a NoSQL database, MongoDB doesn't require defined tables or columns, and each document has flexible structures.

Operations:
- Create:	`insertOne()` / `insertMany()`	- used to add new document(s) to a collection
- Read:	`find()` / `findOne()` - used to get document(s) from a collection
- Update: `updateOne()` / `updateMany()` - used to modify document(s)
- Delete: `deleteOne()` / `deleteMany()` - used to remove document(s)

Before you create your database make sure that you set up the MongoDB server by following the installation steps for your machine: <https://www.mongodb.com/docs/manual/installation/?msockid=2b7cee3aacf767fe2ab7fb85ada96629>

Once that's done, here's how you can get started:
```python
from fastapi import HTTPException
from motor.motor_asyncio import AsyncIOMotorClient
from bson import ObjectId
from models import User, UserIn

# MongoDB Connection
client = AsyncIOMotorClient("mongodb://localhost:27017")
# replace with your connection string, obtained after installing MongoDB

db = client.mydatabase
# fetches your database (replace mydatabase with the name)

users_collection = db.users
# gets user collection in database, or prepares to create it when you insert if it doesn't exist yet

# Helper method to convert MongoDB documents to dicts
def user_helper(user) -> dict:
    return {
        "id": str(user["_id"]),
        "name": user["name"],
        "email": user["email"]
    }

# create user in database
@app.post("/users/", response_model=dict)
async def create_user(user: UserIn):
    new_user = await users_collection.insert_one(user.dict())
    created_user = await users_collection.find_one({"_id": new_user.inserted_id})
    return user_helper(created_user)

# get user from database, if they exist
@app.get("/users/{user_id}", response_model=dict)
async def get_user(user_id: str):
    user = await users_collection.find_one({"_id": ObjectId(user_id)})
    if user:
        return user_helper(user)
    raise HTTPException(status_code=404, detail="User not found")
```
Note that the second argument of each route decorator, `response_model=dict`, specifies the return type as a dict. You can create a model called User and use that instead.

Also, the `inserted_id` part of create_user is an automatically generated property from insert_one(), assigning a unique ObjectId for the document. This is the same id which you will use to access it later in get_user(), but do note that `user_id` has to be converted from a string to an ObjectId.

At this point, you can apply your knowledge of backend concepts to implement the rest of the database functionality for your project's needs, modifying the format to suit the kind of data you're working with.

---

### **Authentication (Bonus)**

Authentication is the process of protecting user data by making sure that certain features are only accessible to the right user. Some of the most common forms of authentication are with a password, multifactor authentication, and OAuth. While beneficial, you're not necessarily expected to implement authentication for this hackathon. In the real world, however, it's an absolute must for building websites that work with user data.

#### **OAuth**
OAuth (Open Authorization) is a framework that lets apps access your data on another service without needing your password. Think using Google or GitHub to sign into platforms.

Here's a breakdown of what happens:
1. User clicks "Login with Google" on your app.
2. Your app redirects to Google (or another provider).
3. User logs in & approves access (like “Yes, allow this app to see my profile info”).
4. Google gives your app an access token.
5. Your app uses that token to call Google APIs (like "get user's email").

If interested, you can learn more at <https://support.google.com/googleapi/answer/6158849?hl=en>