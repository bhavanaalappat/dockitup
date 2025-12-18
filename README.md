# Simple Dockerized Website


#Assignment 1 
This project demonstrates how to serve a basic HTML webpage using **Docker** and **Nginx**.

## Overview
- A simple `index.html` with my name and a short description
- Dockerized using the official **Nginx** image
- Website runs inside a container and is exposed on **port 7070**

## Files
- `index.html` – Static web page
- `Dockerfile` – Builds an Nginx image to serve the page

## How to Run

Build the Docker image:

`docker build -t bhavana-site . `

Run the container:

`docker run -d -p 7070:80 --name bhavana-container bhavana-site`

Access the site:

Browser: http://localhost:7070 or run 

`curl http://localhost:7070`

Cleanup

`docker stop bhavana-container`

`docker rm bhavana-container`
