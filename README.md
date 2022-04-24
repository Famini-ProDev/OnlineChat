# OnlineChat
implement onlineChat with webSocket 

## Features 

- Use the socket.io library to communicate in real-time between the client and the server
- Build a server using the Express Library
- Front development using React.js library

### Technologies:

- BackEnd Side : 
  - Use nodemon to restart the program automatically for changes 
  - Build a server using the Express Library

```
const express = require("express");
const io = require("socket.io");

const app = express();

app.get("/", (req, res) => {
  res.send("hello .hello user");
});


const server = app.listen(3010, (err) => {
  console.log("App Listen to port 3010");
});

const socket = io(server);
const mySocket = socket.of("/socket");

mySocket.on("connection", (socket) => {
  console.log("new User Connected");

  socket.on("newMessage", (message) => {
    console.log(message.msg);
    mySocket.emit("newMessage", { ...message, date: new Date(), id: Math.floor(Math.random() * Math.pow(10, 7)) });
  });
  socket.on("deleteMsg", (id) => {
    console.log(id);
    mySocket.emit("deleteMsg", id);
  });

  socket.on("disconnect", () => {
    console.log("User disconnected")
  })
});
```
- FrontEnd Side:
  - Programming Language: javaScript
  - React hook Components
  - Implementation of component structure using material-ui library
  - Library Css : makeStyles from material-ui/styles
 
## Clinet Project setup

In the project directory, you can run:

```
npm install
# or
yarn install
```
then :
### Client Compiles and hot-reloads for development

```
npm start
# or
yarn start
```
## BackEnd hot-reloads automaticallyt :
```
npm install -g nodemon
```
Execute the Command for restart the program automatically  :
```
nodemon server.js
```
## BackEnd Project setup :

```
yarn dev
or 
npm run dev
```
### About the application:

The purpose of the onlineChat , Online chat design using real time connection with socket.io

