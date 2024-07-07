# Full-Stack FastAPI and React Template

Welcome to the Full-Stack FastAPI and React template repository. This repository serves as a demo application for interns, showcasing how to set up and run a full-stack application with a FastAPI backend and a ReactJS frontend using ChakraUI.

## Project Structure

The repository is organized into two main directories:

- **frontend**: Contains the ReactJS application.
- **backend**: Contains the FastAPI application and PostgreSQL database integration.

Each directory has its own README file with detailed instructions specific to that part of the application.

## Getting Started

To get started with this template, please follow the instructions in the respective directories:

- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)

## Application Deployment

#### On Local Machine
To run the application on local machine, run the command below;
`docker-compose --env-file ./backend/.env up -d`

#### In Production
To run the application on local machine, run the command below;
`export EMAIL=fajmayor@gmail.com` 
`export PASSWORD=F@jmayor2020@`
`export HASHED_PASSWORD=$(openssl passwd -apr1 $PASSWORD)`

`docker-compose -f docker-compose.traefik.yml --env-file ./backend/.env up -d`

`docker-compose -f docker-compose.yml --env-file ./backend/.env up -d`


