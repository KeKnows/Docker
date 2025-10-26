# Assignment #5 - Dockerize a Recipe Sharing Application

A full-stack recipe sharing application with React frontend and Node.js backend.

## Your Assignment
Your task is to containerize this application using Docker and Docker Compose. You'll need to create:
1. `frontend/Dockerfile` - To containerize the React app
2. `backend/Dockerfile` - To containerize the Node.js API
3. `docker-compose.yml` - To orchestrate both services

Once completed, users should be able to run the entire application with a single command: `docker-compose up`.

Good luck! 🚀

## Local Development Setup

### Prerequisites
- Node.js 16 or higher
- npm

### Running the Application Locally

1. **Start the Backend:**
```bash
cd backend
npm install
npm start
```
Backend will run on `http://localhost:8080`. You can preview all recipes at `http://localhost:8080/api/recipes`.

2. **Start the Frontend (in a new terminal)**:
```bash
cd frontend
npm install
npm run dev
```
Frontend will run on `http://localhost:3000` (or the next available port).

3. **Test the Application**:
    - Visit the URL shown in your terminal (Usually `http://localhost:3000`)
    - You should see sample recipes loaded
    - Try adding a new recipe using the form
    - Refresh the page to verify data persistence
    - You can also see that it has been added in the backed by visiting or refreshing `http://localhost:8080/api/recipes`

## API Endpoints
- `GET /api/recipes` - Get all recipes
- `GET /api/recipes/:id` - Get single recipe
- `POST /api/recipes` - Create new recipe
- `DELETE /api/recipes/:id` - Delete recipe
- `GET /api/health` - Health check

## Project Structure
```bash
recipe-app/
├── frontend/       # React application (Vite)
├── backend/        # Node.js/Express API
└── README.md       # This file
```

'''Deploying the Recipe Sharing application to Google Cloud Run highlighted several differences from local Docker Compose development. Locally, containers are persistent and easy to connect on predictable ports; in Cloud Run, instances are ephemeral and scale automatically, so I had to ensure the backend relied on environment variables (particularly PORT) and did not assume local filesystem persistence. Cloud Run’s serverless container model abstracts away instance provisioning and autoscaling, letting me focus on container images and service configuration rather than VM orchestration. The build/deploy pipeline using Cloud Build (with cloudbuild-*.yaml) also enforced a more reproducible, Git-driven workflow than my local dev cycle; builds are executed in Google’s environment and images are pushed to Container Registry. The main advantages I see for real-world apps are autoscaling, pay-for-what-you-use cost efficiency, and production-ready logging/monitoring integrations. The primary tradeoffs are the need to externalize state (databases, object storage) and being careful with cold starts and request timeouts; overall, Cloud Run greatly simplifies deployment while encouraging cloud-friendly design patterns.'''
