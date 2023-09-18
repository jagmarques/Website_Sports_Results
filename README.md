# Real-Time Sports Results Platform

## Introduction
This README provides an overview of a real-time sports results platform developed as a practical project for the Distributed Systems course. The platform allows users to access and receive real-time updates on ongoing sports game results. The project aimed to achieve the following objectives:

- Develop a web system with a data layer and frontend using Spring Boot and Thymeleaf.
- Create a database using Java Persistence Application Programming Interface (JPA).
- Integrate with an external service (api-sports.io) using REST technology to fetch data.

## System Architecture
The system supports three types of users: unregistered users, registered users, and administrators, each with different access controls. All requests pass through a security layer implemented with Spring Security. Registered users send their requests to the UserController, which handles these requests by providing the necessary data. Admins send their requests to the AdminController, which returns various Thymeleaf templates along with essential database data. Unregistered users can send requests to the MainController to perform different actions and view various templates. The MainController also uses an API to fetch external data. There are two layers between the controllers and the database: the Service layer and the Repository Layer. 

## Backend of the Platform
The backend of the platform was developed using Spring Boot, and Spring Data JPA was used for the database. We defined interfaces for our entity classes that extend the CrudRepository Interface, providing operations for specific entity classes. Controllers handle various requests sent through the browser. The user sends a request through the browser, which passes through the security layer and then goes to the appropriate controller. The controller, in turn, calls the service layer through the repository layer, which directly accesses the database for different operations.

Entities used in the project are described in the codebase.

## User Access Control
When users send a request to any URL, it is first checked whether the user is logged in or not. After verifying the user's status, the content accessible to the user is returned. An unregistered user cannot access admin or registered user pages.

## Views Information
Different user types have access to different views, as described below:

- **index.html**: The initial page displayed when the application starts, featuring fictitious data. The navigation bar redirects users to different pages.

- **follow-game.html**: The "Follow Game" option in the navigation bar sends requests to the MainController to display game data.

- **statistics.html**: This page obtains data from the SportsAPI and displays team statistics, including total wins, losses, and draws.

- **signup.html**: Used for user registration, where users provide necessary information for registration.

- **login.html**: After registration, users can log in using this page by providing their credentials. Once logged in, they are directed to the registered user's home page based on their role.

- **admin/home.html**: Presented to administrative users who can perform actions such as managing teams, players, games, and logging out.

- **admin/teams.html**: Admins can create teams by providing team names and logos. After creating a team, they can view, edit, or delete the teams they created.

- **admin/players.html**: On this page, admins can create new players by providing player information such as name, team, date of birth, and position. After creating a player, admins can view, edit, and delete the players they created.

- **admin/games.html**: Admins can view upcoming games, events submitted by registered users, and approve them. Admins can also create games using the "Create Game" button at the top of the page.

- **registered/home.html**: Shown to regular users who can view games and submit events on the "Games" page. Once approved by the admin, events become visible to unregistered users.

- **registered/games.html**: On this page, registered users can view games and submit events for each game.

## How to Run the Application
Follow these steps to run the application:

1. Open the project in IntelliJ Idea.
2. Create a database named "scoredei" in MySQL Workbench.
3. Ensure the database username and password are set to "root."
4. If your MySQL password is different, update it in the "application.properties" file:
   - `spring.datasource.username = your username`
   - `spring.datasource.password = your password`
5. Start the application.
