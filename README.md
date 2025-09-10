PROJECT OVERVIEW

This is  a simple authentication API that supports user signup, login, logout (with token revocation), and profile retrieval.

SETUP STEPS

1. Clone the repo

	Paste in terminal

git clone https://github.com/ArjelAaran/lab-auth.git
cd lab-auth

2. Install dependencies
	
	Paste in terminal

npm install

3. Set up database

- Create a database in MySQL (lab_auth)
- Create the tables:

CREATE DATABASE IF NOT EXISTS lab_auth;

USE lab_auth;

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  email VARCHAR(255) NOT NULL UNIQUE,
  password_hash VARCHAR(255) NOT NULL,
  full_name VARCHAR(255),
  role ENUM('student','admin') DEFAULT 'student',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE revoked_tokens (
  id INT AUTO_INCREMENT PRIMARY KEY,
  jti VARCHAR(64) NOT NULL UNIQUE,
  expires_at DATETIME NOT NULL
);

4. Copy .env.example and RENAME to .env

	Make sure to update database credentials accordingly

HOW TO RUN

Go to root terminal and enter:

	npm run dev

Server will run at http://localhost:[PORT]

LIST OF ENDPOINTS

Register a new user - /api/auth/signup

Login and receive a JWT - /api/auth/login

Revoke the current JWT - /api/auth/logout

Get the logged-in user's profile - api/profile
