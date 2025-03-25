# Movies API in Go

A simple RESTful API for managing movies, built using Go and Gorilla Mux. This API performs all CRUD (Create, Read, Update, Delete) operations on movies.

## Features
- List all movies (`GET /movies`)
- Retrieve a specific movie (`GET /movies/{id}`)
- Add a new movie (`POST /movies`)
- Update an existing movie (`PUT /movies/{id}`)
- Delete a movie (`DELETE /movies/{id}`)

## Prerequisites
- Install [Go](https://golang.org/dl/) (version 1.21 or later recommended)

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/movies-app.git
   cd movies-app
   ```
2. Initialize a Go module (if not already initialized):
   ```sh
   go mod init movies-app
   ```
3. Install dependencies:
   ```sh
   go get github.com/gorilla/mux
   ```
4. Build the application:
   ```sh
   go build
   ```

## Usage
### Running the Server
Execute the following command:
```sh
go run main.go
```
The server will start on `http://localhost:8000/`.

### API Endpoints
This API supports full CRUD operations:

#### 1. Get All Movies (Read)
**Request:**
```sh
GET /movies
```
**Response:**
```json
[
  {
    "id": "1",
    "isbn": "438227",
    "title": "Movie One",
    "director": { "firstName": "John", "lastName": "Doe" }
  }
]
```

#### 2. Get a Movie by ID (Read)
**Request:**
```sh
GET /movies/{id}
```
**Response:**
```json
{
  "id": "1",
  "isbn": "438227",
  "title": "Movie One",
  "director": { "firstName": "John", "lastName": "Doe" }
}
```

#### 3. Create a Movie (Create)
**Request:**
```sh
POST /movies
Content-Type: application/json

{
  "isbn": "123456",
  "title": "New Movie",
  "director": { "firstName": "Jane", "lastName": "Doe" }
}
```
**Response:**
```json
{
  "id": "random-generated-id",
  "isbn": "123456",
  "title": "New Movie",
  "director": { "firstName": "Jane", "lastName": "Doe" }
}
```

#### 4. Update a Movie (Update)
**Request:**
```sh
PUT /movies/{id}
Content-Type: application/json

{
  "isbn": "654321",
  "title": "Updated Movie",
  "director": { "firstName": "Updated", "lastName": "Director" }
}
```
**Response:**
```json
{
  "id": "1",
  "isbn": "654321",
  "title": "Updated Movie",
  "director": { "firstName": "Updated", "lastName": "Director" }
}
```

#### 5. Delete a Movie (Delete)
**Request:**
```sh
DELETE /movies/{id}
```
**Response:**
```json
[]
```

## Error Handling
- If an unsupported route is requested, the server will return `404 not found`.
- If invalid data is sent in `POST` or `PUT`, a parsing error will be returned.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
