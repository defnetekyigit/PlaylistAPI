# Playlist API

A simple RESTful Playlist API built using **Node.js + Express + TypeScript**, documented with **Swagger**, and deployed publicly on **Google Cloud Run**.  
This project was developed as part of **Assignment – SE4458 Software Construction**.

---

## Live Demo

- **Deployment (Swagger UI):**  
 [https://playlist-api-476914-europe-west1.run.app/swagger](https://playlist-api-476914-europe-west1.run.app/swagger)

- **API Base URL:**  
  [https://playlist-api-476914-europe-west1.run.app/api/songs](https://playlist-api-476914-europe-west1.run.app/api/songs)

---

## Source Code

- **GitHub Repository:**  
 [https://github.com/defnetekyigit/PlaylistAPI](https://github.com/defnetekyigit/PlaylistAPI)


## Project Overview

This API allows users to **create, update, delete, search, and list songs** in a playlist.  

### Features
- CRUD operations (`GET`, `POST`, `PUT`, `DELETE`)
- Search songs by name or singer
- Swagger documentation at `/swagger`
- Containerized with Docker
- Deployed via Google Cloud Build → Cloud Run

---

## Technologies Used
- **Node.js** + **Express.js**
- **TypeScript**
- **Swagger UI** (`swagger-jsdoc`, `swagger-ui-express`)
- **Docker**
- **Google Cloud Build / Cloud Run**

---

## API Endpoints

| Method | Endpoint | Description |
|--------|-----------|-------------|
| `GET` | `/api/songs` | Get all songs |
| `GET` | `/api/songs/{id}` | Get a song by ID |
| `POST` | `/api/songs` | Add a new song |
| `PUT` | `/api/songs/{id}` | Update an existing song |
| `DELETE` | `/api/songs/{id}` | Delete a song |
| `GET` | `/api/songs/search?q={keyword}` | Search songs by name or singer |

---

## Design & Assumptions

- **In-memory data store:**  
  The playlist is maintained in a local array (`playlist[]`), reset on server restart.
- **Unique IDs:**  
  IDs are generated using timestamps (`Date.now()`).
- **Validation:**  
  `name` and `singer` fields are required for new songs.
- **Simple structure:**  
  Focus is on RESTful design and deployment 
- **CORS Enabled:**  
  Swagger can execute requests directly in the browser.

---

## Issues Encountered

- Cloud Build initially failed due to `tsc: Permission denied`, fixed by installing `typescript` globally in Dockerfile.
- Swagger didn't detect routes at first, solved by updating `apis` path to `src/routes/*.ts`.
- Added `cors` middleware to allow browser execution in Swagger UI.
- `node_modules` excluded from GitHub with `.gitignore`.


## Deployment Summary

- Built Docker image using Google Cloud Build  
  ```bash
  gcloud builds submit --tag gcr.io/playlist-api-476914/playlist-api
