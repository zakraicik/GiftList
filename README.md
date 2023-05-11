# Gift List

This application is a simple client-server application that simulates a gift-giving scenario based on a "nice list" of names.**This application demonstrates a simplified example of using a Merkle tree and proof verification to grant gifts to individuals based on their presence in the nice list.**

The client-side code is responsible for making a request to the server to request a gift based on a provided name. It uses Axios, an HTTP client library, to send a POST request to the server's /gift endpoint. The request includes the name and a proof generated from a Merkle tree. Upon receiving the response from the server, the client-side code logs the received gift to the console.

The server-side code is an Express.js server that listens on port 1225. It exposes a single POST route at /gift. When a POST request is received, the server retrieves the name and proof from the request body. It then uses a verification function, verifyProof, to check if the provided name exists in the nice list based on the proof and a pre-defined Merkle root. If the name is found in the list, the server responds with the message "You got a toy robot!". Otherwise, if the name is not found, the server responds with the message "You are not on the list :(".

To get started with the repository, clone it and then run `npm install` in the top-level directory to install the depedencies.

## Server

You can run the server from the top-level directory with `node server/index`. This file is an express server which will be hosted on port 1225 and respond to the client's request.

## Requsting a gift

Running `node server/index "Shelly Toy"` should return `{ gift: 'You got a toy robot!' }`.

However, running `node server/index "Zak"` should return `{ gift: 'You are not on the list :(' }`.
