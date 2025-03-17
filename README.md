# CSC3916 Assignment 3 - Web API with MongoDB

## Purpose
This assignment is aimed at gaining experience with MongoDB and building a secure Node.js Web API that interacts with a NoSQL database. The application uses JWT authentication for protecting routes and performing CRUD operations on movies and user data.

## Features
- **User Authentication**: Implements signup and signin functionality with JWT token-based authentication.
- **Movie Collection**: CRUD operations on movies, which include:
  - Title (string, required, indexed)
  - Release Date
  - Genre (e.g., Action, Adventure, Comedy, Drama, Fantasy, Horror, Mystery, Thriller, Western, Science Fiction)
  - Array of actors (minimum of three actors with their respective character names)
- **React Frontend**: A React-based Single Page App (SPA) for user signup and signin.

## API Routes
### User Routes
- **POST /signup**: Creates a new user with name, username, and password.
- **POST /signin**: Authenticates a user and returns a JWT token.

### Movie Routes
- **GET /movies**: Returns all movies in the database.
- **POST /movies**: Adds a new movie to the collection (requires valid token).
- **GET /movies/:title**: Returns a specific movie by its title.
- **PUT /movies/:title**: Updates a movie based on its title (requires valid token).
- **DELETE /movies/:title**: Deletes a specific movie by its title (requires valid token).

### Authentication
All movie-related endpoints are protected and require a valid JWT token obtained from the signin route.

## Setup Instructions

### Prerequisites
- Node.js installed
- MongoDB Atlas account for a cloud database (or use a local MongoDB instance)
- Heroku or Render account for deployment

### Installation
1. Clone the repository:
   ```bash
   git clone <YOUR_GITHUB_REPO_URL>
   cd CSC3916_Assignment3
2. Install dependencies:
   npm install
3. Set up the environment variables: Create a .env file in the root directory with the following variables:
   SECRET_KEY=<your_secret_key>
   DB=<your_mongo_database_url>
4. Run the application locally:
   npm start
   
### API Testing
The API can be tested using Postman. Follow these steps:

#### Sign Up a User:
- Make a `POST` request to `/signup` with a JSON body containing `name`, `username`, and `password`.

#### Sign In a User:
- Make a `POST` request to `/signin` with a JSON body containing `username` and `password`.
- Save the returned JWT token.

#### Testing Movie Routes:
- **Create a Movie**: Make a `POST` request to `/movies` with a JSON body containing `title`, `releaseDate`, `genre`, and `actors` (at least three actors).
- **Get All Movies**: Make a `GET` request to `/movies`.
- **Update a Movie**: Make a `PUT` request to `/movies/:title` with the updated movie data.
- **Delete a Movie**: Make a `DELETE` request to `/movies/:title`.

#### Error Handling:
- Handle cases where the user already exists during signup.
- Handle missing data for movie creation (e.g., missing actors, title, or genre).

### Deployment
The API has been deployed on [Heroku/Render] and can be accessed at the following URL: https://csc3916-assignment3-9aaz.onrender.com

### React App
The React SPA has been updated to interact with the API. The app allows users to sign up, sign in, and view or manage movies. You can find the React app in the 'Movie_Frontend_React` repository.

### Postman Collection
The Postman collection for testing is available at the following link:  
[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://god.gw.postman.com/run-collection/41740081-0429bafc-f3de-4b06-bfae-c8141a26d247?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D41740081-0429bafc-f3de-4b06-bfae-c8141a26d247%26entityType%3Dcollection%26workspaceId%3Dbd7f337b-a9cf-47ae-8848-c40a738c3714#?env%5BNew%20Environment%5D=W3sia2V5IjoiZWNob19ib2R5IiwidmFsdWUiOiIiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiZGVmYXVsdCJ9LHsia2V5IjoidG9rZW4iLCJ2YWx1ZSI6IiIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJhbnkifV0=)
