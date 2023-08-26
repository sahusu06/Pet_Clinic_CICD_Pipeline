# Pet_Clinic_CICD_Pipeline

Welcome to the Pet Clinic project repository! This project aims to create a simple CI/CD pipeline to deploy a web application for managing a pet clinic's operations.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
- [CI/CD Pipeline](#cicd-pipeline)

  
## Overview

The Pet Clinic project is a web application developed to assist in managing various aspects of a pet clinic, including pet records, appointments, and more.

## Features

- User-friendly interface for managing pet clinic operations.
- Create, update, and view pet records.
- Schedule and manage appointments.

## Technologies Used

Before getting started, make sure you have the following tools and services set up:

- Docker: Used for containerizing the application and providing consistent environments.
- SonarQube: Utilized for static code analysis and continuous inspection of code quality.
- Postgres Database: Store data related to code analysis,generated from SonarQube application.
- Ansible: Employed for automated deployment and configuration management.
- Nexus: Used as a repository for storing artifacts and Docker images.
- Two EC2 Instances with min 4 GB RAM.

## Getting Started

1. Repository used:
   - git clone https://github.com/sahusu06/spring-petclinic.git
2. Install Docker, and run Jenkins container.
3. Run Nexus,SonarQube,Postgres DB and Jenkins containers on the build server.
4. Docker Compose to start Nexus,SonarQube and Postgres DB containers have been provided in the repository.
5. Ansible Playbooks have been created to move Jar artefcats,create docker images and push image to Nexus repoitory.
   
