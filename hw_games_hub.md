1. What is responsible for defining the routes of the `games` resource?

The games resource is first exported as data from GamesGrid.vue. The routes are defined in server.js, using the createRouter function exported from create_router.js.

2. What do you notice about the folder structure?  Whats the client responsible for? Whats the server responsible for?

Client - responsible for front end (holds App.vue, multiple Vue components, Vue events visible to the client using the page, CSS styling to organise how the app appears to the user). Also fetches the games API in GamesService.js. Running on localhost port 8080 (Vue development environment)

Server - responsible for back end (db folder with seed data for MongoDB database games_hub, RESTful routes defined in server.js). Running on localhost port 3000 (Express server)

3. What are the the responsibilities of server.js?

- Connects to MongoDB database games_hub
- Creates gamesRouter which defines the routes of the 'games' resource using the createRouter function from create_router.js

4. What are the responsibilities of the `gamesRouter`?

- Passes gamesCollection as the parameter for the createRouter function
- Listens for server actions on port 3000, specifically regarding the data gamesRouter uses from /api/games/ 

5. What process does the the client (front-end) use to communicate with the server?

Fetches data from the games API in GamesServices.js. This data is used by the server.

6. What optional second argument does the `fetch` method take? And what is it used for in this application? Hint: See [Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) on the MDN docs

After fetching the games API url (defined in GamesServices as a variable named baseURL), the fetch method takes a Javascript object as a second argument which is then converted into a JSON strong using .stringify. In the application this is applied to POST routes.

7. Which of the games API routes does the front-end application consume (i.e. make requests to)?

- GET to display the games data
- POST to create new game data
- PUT to update game data
- DELETE to delete game data

8. What are we using the [MongoDB Driver](http://mongodb.github.io/node-mongodb-native/) for?

This is a node.js driver for MongoDB - we are using it to connect our Vue app to our MongoDB database games_hub

9. Why do we need to use [`ObjectId`](https://mongodb.github.io/node-mongodb-native/api-bson-generated/objectid.html) from the MongoDB driver?

ObjectID is used to select a specific item from the database using its unique id