# Forum Project

A web-based communication platform built from scratch using **Go**, **SQLite**, and **Docker**. This project implements core forum features including user authentication, post creation, categorization, and a like/dislike system, all without relying on external frontend frameworks.

## 📋 Table of Contents
- [Objectives](#objectives)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Database Structure](#database-structure)
- [Installation & Usage](#installation--usage)
- [Testing](#testing)
- [License](#license)

## 🎯 Objectives
This project focuses on understanding the fundamental mechanics of web development:
*   **Web Fundamentals:** Handling HTTP requests, sessions, and cookies.
*   **Authentication:** Implementing secure user registration and login flows with encryption.
*   **Data Persistence:** Managing relational data using SQLite and raw SQL queries.
*   **Containerization:** Dockerizing a full-stack Go application for consistent deployment.

## ✨ Features

### 🔐 Authentication & Security
*   **User Registration:** Secure sign-up with email, username, and password.
*   **Encrypted Passwords:** Passwords hashed using `bcrypt` before storage.
*   **Session Management:** Cookie-based sessions with expiration (UUID support included).
*   **Input Validation:** Prevention of duplicate emails/usernames.

### 💬 Communication
*   **Create Posts:** Registered users can create threads.
*   **Categories:** Posts can be tagged with multiple categories (e.g., Tech, General, Help).
*   **Comments:** Users can discuss topics via nested comments.
*   **Visibility:** Public read access for guests; write access restricted to registered users.

### 👍 Interactions
*   **Likes & Dislikes:** Users can react to both posts and comments.
*   **Live Counters:** Real-time display of like/dislike counts visible to all.

### 🔍 Filtering
*   **Category Filter:** Browse posts by specific sub-forums.
*   **User Activity:** Filter to see "My Created Posts" and "My Liked Posts".

## 🛠 Technology Stack

| Component | Technology |
| :--- | :--- |
| **Backend** | Go (Golang) |
| **Database** | SQLite3 (`go-sqlite3`) |
| **Security** | Bcrypt (`x/crypto/bcrypt`) |
| **Session ID** | UUID (`gofrs/uuid`) |
| **Frontend** | HTML5, CSS3 (No JS Frameworks) |
| **Deployment** | Docker |

## 🗄 Database Structure
The project uses a relational SQLite database. Below is a high-level overview of the schema:

*   **Users:** Stores credentials (id, username, email, hashed_password).
*   **Sessions:** Manages active logins (user_id, cookie_uuid, expiry).
*   **Posts:** Stores thread content (id, user_id, title, content).
*   **Comments:** Stores replies (id, post_id, user_id, content).
*   **Categories:** Defined tags for posts.
*   **Likes:** Tracks user reactions (user_id, post_id/comment_id, type).

## 🚀 Installation & Usage

### Prerequisites
*   [Docker](https://docs.docker.com/get-docker/) installed on your machine.

### 1. Clone the Repository
git clone https://github.com/mohammedouchkhi/forum.git

cd forum


### 2. Build the Docker Image
Build the project image using the provided Dockerfile. naming it `forum-app`.
docker build -t forum-app .


### 3. Run the Container
Run the application in a container, mapping port 8080.
docker run -p 8080:8080 --name my-forum-container forum-app

*The application will now be accessible at `http://localhost:8080`.*

### 4. Stop & Remove
To stop the running server:
docker stop my-forum-container
docker rm my-forum-container

## 📜 License
This project is part of the Zone01 Oujda curriculum.
