# Gamebuildr Architecture

The Gamebuildr architecture is comprised of the main web app, which hosts the front-end and api, and the microservices.

This section will give a brief overview of how the system works and the data flows from the front-end to the microservices.

### Front-end to Microservices

When the user interacts with the web app there are two routes that information is gathered and given to a user. First, if the user is manipulating system data, such as projects or generic information, the web app will communicate directly with the web api. In many cases the web api will gather information from the database and return it directly to the front-end.

The second notable interaction is when a user adds in a new buildr (which is either adding source code or running an engine build). When this happens the system will send a message to Amazon SNS to notify the microservices that the user wants to create a new buildr. The microservices will then re-route the message to the correct endpoint for it to be processed.

### Mircroservice interaction

To manage messages coming from Amazon SNS we use two specific systems. First, the __Dave__ microservice will redirect aAmazon SNS messages either to our source control system __Gogeta__ or our game engine service __Mr. Robot__. Due to the fact that Mr. Robot with the corresponding engine is contained inside Docker we also utilize another microservice __Hal__ to spin up and down requested docker containers directly from docker.

In other words the flow looks like:

1. Message is sent from front-end to Amazon SNS.

2. Dave is watching for messages and reads the message off the queue.

3. (a) If the message is for source control then Gogeta will read the message and process.

3. (b) If the message is for a new build then Hal will read the message off the queue, process the engine version and id, and start the correct docker container.

