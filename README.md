


# Assignment 1 
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


# Assignment 2 



## Overview
This project demonstrates how to deploy **two Docker containers** that communicate with each other using a **custom Docker network**.

- A **static Nginx web server** serves an HTML page.
- A **simple API container** responds with a text message.
- The web container connects to the API container using **Docker’s internal DNS** (container name resolution).

---

## Technologies Used
- Docker
- Docker Networking
- Nginx
- `hashicorp/http-echo`

## Setup Instructions

1. Create a Custom Docker Network

`docker network create webnet`


2. Run an nginx container

  docker build -t web-image 

  `docker run -d --name web --network webnet -p 8080:80 web-image`
  


3. Create a simple API container:

`docker run -d --name api --network webnet hashicorp/http-echo -text="Hello from API"`

4.  The html file should include a button that fetches /api

5. Test that the web container can reach the API container using container name:

`http://api:5678`

6. Demonstrate connectivity using curl inside the web container:

`docker exec -it web curl http://api:5678`

