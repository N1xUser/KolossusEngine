# Mission Explorer: Visualizer (Kolossus)

Mission Explorer is a web-based platform that allows users with or without an academic background to access and interact with high-resolution lunar imagery and 3D crater panoramas from NASA's Apollo missions. The application provides an immersive experience for exploring the lunar surface, complete with an AI-powered assistant, "CraterBot," to answer questions and provide context about the missions.

## Features

*   **High-Resolution Image Viewer:** Explore massive lunar images with a dynamic tiling system that allows for smooth zooming and panning.
*   **3D Crater Explorer:** Immerse yourself in 360° panoramic views of lunar craters.
*   **Investigation Lab:** Select and stitch multiple images together to create panoramic views.
*   **AI-Powered Chat Assistant (CraterBot):** Get information and ask questions about the Apollo 15, 16, and 17 missions, as well as the lunar features you are observing.
*   **Admin Panel:** A dedicated interface for uploading and managing lunar imagery and crater panoramas.

## Technologies Used

### Frontend

*   **Next.js:** A React framework for building server-side rendered and static web applications.
*   **React:** A JavaScript library for building user interfaces.
*   **TypeScript:** A typed superset of JavaScript that compiles to plain JavaScript.
*   **Tailwind CSS:** A utility-first CSS framework for rapid UI development.
*   **shadcn/ui:** A collection of re-usable UI components.

### Backend

*   **Flask:** A lightweight WSGI web application framework in Python.
*   **Pillow:** A powerful image processing library for Python.
*   **OpenCV:** A library of programming functions mainly aimed at real-time computer vision.
*   **Google Generative AI:** Powers the CraterBot assistant.

## Setup and Installation

### Prerequisites

*   Node.js and npm (or yarn)
*   Python 3.7+ and pip
*   A Google Generative AI API Key

### Backend Setup

1.  **Clone the repository:**
    ```bash
    git clone https://your-repository-url.git
    cd your-repository-name
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the required Python packages:**
    ```bash
    pip install -r requirements.txt
    ```
    *(Note: You will need to create a `requirements.txt` file with the necessary Python libraries: Flask, Flask-Cors, Pillow, opencv-python-headless, numpy, google-generativeai)*

4.  **Set up your Google Generative AI API Key:**
    *   Open the `server_side.py` file.
    *   Replace `"AIzaSyArVogFxTiuDR9nlFoMigCkP9jfZ-SPJjs"` with your actual Gemini API key in the `GEMINI_API_KEY` variable.

5.  **Run the Flask server:**
    ```bash
    python server_side.py
    ```
    The backend server will start on `http://localhost:5000`.

### Frontend Setup

1.  **Navigate to the frontend directory** (assuming your Next.js project is in a `frontend` subdirectory):
    ```bash
    cd frontend
    ```    *(Note: Based on the provided files, the Next.js components are in the root. You would typically have a `package.json` in the root of your frontend project.)*

2.  **Install the required npm packages:**
    ```bash
    npm install
    ```

3.  **Run the Next.js development server:**
    ```bash
    npm run dev
    ```
    The frontend application will be accessible at `http://localhost:3000`.

## Usage

*   **Home Page:** Provides an introduction to the project and links to the main sections.
*   **Apollo Missions:** Browse through the Apollo 15, 16, and 17 missions and explore their available imagery.
*   **Crater Explorer:** View and interact with 3D panoramic images of lunar craters.
*   **Dynamic Image Viewer:** Pan and zoom through high-resolution lunar images. Click on crater hotspots to interact with CraterBot.
*   **Investigation Lab:** Select a mission and choose images to stitch together into a panoramic view.
*   **Admin Panel:** Access the admin panel at a designated route to upload new images and crater panoramas.

## API Endpoints

### Chat

*   `POST /api/init`: Initializes a new chat session.
*   `POST /api/select-crater`: Selects a crater for the chat context.
*   `POST /api/chat/stream`: Streams a response from the CraterBot.

### Image and Tile Management

*   `POST /api/upload`: Uploads a new high-resolution image and generates tiles.
*   `GET /api/missions/<mission>/images`: Retrieves a list of images for a specific mission.
*   `GET /api/tiles/<mission>/<image_name>/<zoom>/<col>_<row>.jpg`: Retrieves a specific image tile.
*   `GET /api/preview/<mission>/<image_name>`: Retrieves a preview of an image.
*   `GET /api/metadata/<mission>/<image_name>`: Retrieves metadata for a specific image.
*   `GET /api/tile-info/<mission>/<image_name>`: Retrieves tile information for a specific image.

### Crater Management

*   `POST /api/craters/upload`: Uploads a new crater panorama.
*   `GET /api/craters/list`: Retrieves a list of all crater panoramas.
*   `GET /api/craters/<crater_id>`: Retrieves information for a specific crater.
*   `GET /api/craters/image/<filename>`: Retrieves the full-size image for a crater.
*   `GET /api/craters/thumbnail/<filename>`: Retrieves the thumbnail for a crater.
*   `DELETE /api/craters/<crater_id>`: Deletes a crater.

### Investigation

*   `POST /api/investigation/stitch`: Stitches a series of images together into a panorama.
