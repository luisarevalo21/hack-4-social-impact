# Backend API

A FastAPI-based backend server for the application.

## Prerequisites

- Python 3.13 or higher
- pip (Python package installer)

## Setup

1. **Navigate to the backend directory**

   ```bash
   cd main/backend
   ```

2. **Create a virtual environment (optional but recommended)**

   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On macOS/Linux
   # or
   .venv\Scripts\activate     # On Windows
   ```

3. **Install dependencies**

   ```bash
   pip install fastapi uvicorn[standard]
   ```

   Or if you have the project configured with pyproject.toml:

   ```bash
   pip install -e .
   ```

## Running the Server

### Development Mode (with auto-reload)

```bash
uvicorn main:app --reload
```

### Production Mode

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

### Custom Host and Port

```bash
uvicorn main:app --host 127.0.0.1 --port 3001 --reload
```

## Accessing the API

- **API Base URL**: `http://localhost:8000`
- **Interactive API Documentation (Swagger)**: `http://localhost:8000/docs`
- **Alternative API Documentation (ReDoc)**: `http://localhost:8000/redoc`
- **OpenAPI Schema**: `http://localhost:8000/openapi.json`

## Available Endpoints

- `GET /` - Returns a "Hello World" message

## Development

### Adding New Endpoints

Add new routes to `main.py`:

```python
@app.get("/new-endpoint")
async def new_endpoint():
    return {"message": "This is a new endpoint"}
```

### Environment Variables

Create a `.env` file in the backend directory for environment-specific configurations:

```env
DEBUG=True
HOST=0.0.0.0
PORT=8000
```

### Project Structure

```
backend/
├── main.py          # FastAPI application entry point
├── pyproject.toml   # Project configuration and dependencies
├── README.md        # This file
└── .env            # Environment variables (create if needed)
```

## Troubleshooting

- **Port already in use**: Change the port using `--port` flag or kill the process using the port
- **Module not found**: Make sure you're in the correct directory and dependencies are installed
- **Permission denied**: On macOS/Linux, you might need to use `sudo` or check file permissions

## Next Steps

- Add database integration
- Implement authentication
- Add logging and monitoring
- Create additional API endpoints
- Add tests
