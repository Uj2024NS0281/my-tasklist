# Tasklist

A simple to-do list app built with vanilla HTML, CSS, and JavaScript, containerized with Docker and served via Nginx. Tasks are saved in the browser using localStorage, so they persist even after a refresh.

## Features

- Add, complete, and delete tasks
- Tasks persist between sessions (localStorage)
- Live counter showing remaining (incomplete) tasks
- "Clear completed" button to remove finished tasks in bulk
- Clean, dark-themed UI
- Keyboard support (press Enter to add a task)

## Tech Stack

- **Frontend:** HTML, CSS, JavaScript
- **Server:** Nginx (Alpine)
- **Containerization:** Docker

## Project Structure

```
.
├── Dockerfile      # Instructions to build the container image
├── index.html      # The tasklist app (markup, styling, and logic)
└── README.md
```

## Running the App

### Option 1: Pull and run from Docker Hub

```bash
docker pull uj2024ns0281/mytasklist:v1
docker run -p 8080:80 uj2024ns0281/mytasklist:v1
```

Then open **http://localhost:8080** in your browser.

### Option 2: Build from source

Clone this repository, then from the project folder:

```bash
docker build -t mytasklist .
docker run -p 8080:80 mytasklist
```

Then open **http://localhost:8080** in your browser.

## How It Works

The Dockerfile uses a lightweight `nginx:alpine` base image to serve the static `index.html` file. Nginx handles the app on port 80 inside the container, which is mapped to port 8080 on the host machine.

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```

## Known Limitations

- Tasks are stored per-browser using localStorage, not a shared database. Clearing browser data or switching devices/browsers will not carry tasks over.

## Docker Hub

Public image: [uj2024ns0281/mytasklist](https://hub.docker.com/r/uj2024ns0281/mytasklist)

## Author

Andrew Agom
