SIM Card Activation Service Documentation

Table of Contents
1.	Introduction
2.	System Requirements
3.	Database Schema
4.	API Endpoints
5.	Error Handling
6.	Deployment
7.	Testing
8.	Assumptions and Decisions

Introduction
The SIM Card Activation Service is a simple web application built using Flask and SQLite. It provides a RESTful API for activating and deactivating SIM cards, as well as retrieving SIM card details.

System Requirements
	Python 3.8 or later
	Flask 2.0 or later
	MySQL 3.32 or later
	pip 20.0 or later

Database Schema
The database schema consists of a single table, sim_cards, with the following columns:
Column Name	Data Type	Description
sim_number	TEXT	Unique identifier for the SIM card
phone_number	TEXT	Phone number associated with the SIM card
status	TEXT	Status of the SIM card (active or inactive)
activation_date	TIMESTAMP	Date and time the SIM card was activated



API Endpoints
1)	Activate SIM Card
	Endpoint: /activate
	Method: POST
	Input: {"sim_number": "your_sim_number"}
	Response: {"message": "SIM card activated successfully"}
	Description: Activates a SIM card by setting its status to active and recording the activation date.

2)	Deactivate SIM Card
	Endpoint: /deactivate
	Method: POST
	Input: {"sim_number": "your_sim_number"}
	Response: {"message": "SIM card deactivated successfully"}
	Description: Deactivates a SIM card by setting its status to inactive.

3)	Get SIM Details
	Endpoint: /sim-details/<sim_number>
	Method: GET
	Response: {"sim_number": "your_sim_number", "phone_number": "your_phone_number", "status": "active/inactive", "activation_date": "activation_date"}
	Description: Retrieves the details of a SIM card.

Error Handling
The API endpoints handle the following error scenarios:
	SIM card not found (404)
	SIM card already in the desired state (400)
	Required input fields missing or invalid (400)

Deployment
The application can be deployed on any open-source platform like Heroku or Netlify.

Testing
You can test the API endpoints using a tool like Postman or cURL.

Assumptions and Decisions
	The application assumes that the SIM card number is unique and cannot be changed once created.
	The application uses a simple SQLite database for storing SIM card data. In a production environment, a more robust database like PostgreSQL or MySQL would be recommended.
	The application does not implement authentication or authorization. In a production environment, this would be a critical security feature to implement.

API Documentation
The API documentation is available in the README.md file.

Code Structure
The code is structured as follows:
	app.py: The main application file that defines the API endpoints.
	schema.sql: The database schema file that defines the sim_cards table.
	requirements.txt: The file that lists the dependencies required by the application.

Commit Messages
The commit messages follow the standard format of [type]([optional scope]): [short description].

API Validation
The API endpoints validate the input data to ensure that it conforms to the expected format.

Security Considerations
The application does not implement any security features like authentication or authorization. In a production environment, this would be a critical security feature to implement.
