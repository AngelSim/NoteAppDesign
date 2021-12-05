# Note Application System Design
The following page is an example design of a "Note app" web application. 
asdasda

## 1. Describe high level design
In order to achieve a clean system design, with the possibility of being able to be extended in the future with ease, we can implement the following the design style:
 - We will create 4 layers. Each layers will present a collection of system components, important to the application, managed in a way that the design is dependent on the business rules of our domain. Consider the following diagram:
<img src="https://user-images.githubusercontent.com/13337992/144759536-45dd312d-a293-45bc-8901-bac03e628955.png" width="500" height="500">
2 important observations can be made here: the 4 layers of the application and their dependencies with each other. Note the direction of the dependency arrows.
 - Definition of each layer:

1. Domain - Represents the domain objects of our application. Only plain objects are contained here, whithout any sort of knowledge about concrete frameworks and technologies. This layer does not depend on any of the other layers or any frameworks. In our case, there could be the following entities: "Note" and "User"
2. Application - Represents the business actions of our application in the form of interfaces without concrete implementation. The point of this layer is to give a high-level declaration of the business rules of our domain, without knowing the specifics. This layer depends only on the Domain layer, as it uses the domain entites to declare how the application should handle those entitites. In our case, this layer contains interface definitions of the following actions: "Validate User", "User enters a block of text", "Save button saves the note", "User can see a list of saved notes", "User can delete a saved note"
3. Infrastructure - Represents the layer, that will contain concrete implementation of the interfaces defined in the Application layer. These implementations can use frameworks for specific technologies for example: managing a database or other types of storage, parsing documents in various data formats among others. This layer depends on both the Application and Domain layers, as it uses the entities from the domain layers and also implements the interfaces of the Application layer. In our case, this layer can contain the specific details of the database we are using to store and retreive the Notes and Users.
4. Presentation - this layer represents the "outer wrap" of our application, the part with whcih the users/clients can directly interact with in order to use the app. This layer is on the same level of the Infrastructure layer as tend to they overlap in their concept. The presentation layer can be anything that allows users to interact with the app: Web UI, public REST API, Desktop application framework, Mobile app framework. In our case, this is going to be a Web UI is the requirement is "the note app runs in a client browser".

## 2. Web App UI
 - The way the Web UI will interact with the application backend is that it will use HTML+CSS pages in order to retreive the Notes from the Users, and then it will use JavaScrypt in order to send/retreive Note information from the backend server through HTTP REST communication.
 - Validation will be a combination of client-side and server side validation. The Web UI app can validate whether the user input data is correct using JavaScript, HTML5 also has some validation functionalities. The server-side validation will be responsible for authorizing the User.

## 3. Data Model
The Note entity can look like the following:

<img width="192" alt="Screenshot 2021-12-05 at 22 01 49" src="https://user-images.githubusercontent.com/13337992/144761918-8a205749-41d2-47b2-ad59-cada90de0667.png">

## 4. Restful API
Examples of REST API operations:

```
GET /notes - Retrieves a list of notes
GET /notes/5 - Retrieves a specific note
POST /notes - Creates a new note
PUT /notes/5 - Updates note #5
PATCH /notes/5 - Partially updates note #5
DELETE /notes/5 - Deletes note #5
```

## 5. Web Server
This has been described in the 1st paragraph "Describe high level design"
