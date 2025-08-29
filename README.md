#PPT Generator

This app lets anyone turn bulk text, markdown, or prose into a fully formatted PowerPoint presentation that matches their chosen template’s look and feel.

## Features
- Paste or type a large block of text
- Enter guidance for tone, structure, or use case
- Provide your own LLM API key (never stored)
- Upload a PowerPoint template or presentation (.pptx/.potx)
- Download the newly generated presentation

## Tech Stack
- Frontend: React, Tailwind CSS
- Backend: FastAPI (Python)
- PowerPoint manipulation: python-pptx

## Setup Instructions

### Backend (FastAPI)
1. Navigate to the `backend` folder:
	```powershell
	cd backend
	python -m venv venv
	.\venv\Scripts\activate
	pip install fastapi uvicorn python-pptx requests
	uvicorn main:app --reload
	```
2. The API will run at `http://localhost:8000`.

### Frontend (React)
1. Navigate to the `frontend` folder:
	```powershell
	cd frontend
	npm install
	npm start
	```
2. The app will run at `http://localhost:3000`.

## Usage
1. Start both backend and frontend servers.
2. Open the frontend in your browser.
3. Paste your text, enter guidance, provide your LLM API key, and upload a PowerPoint template.
4. Click "Generate & Download Presentation" to receive your formatted `.pptx` file.

## Deployment
- Frontend: Deploy to Vercel, Netlify, or similar static hosting.
- Backend: Deploy to Render, Railway, or any Python web host.

## Technical Write-up

**How input text is parsed and mapped to slides:**
The backend uses an LLM (such as OpenAI, Anthropic, or Gemini) to analyze the user’s input text and guidance. The LLM is prompted to split the text into logical slide sections, typically returning a markdown or structured response with slide titles and content. This response is parsed into a list of slides, each with a title and body, ensuring the number and structure of slides matches the content and user intent.

**How the app applies the visual style and assets of the template:**
The uploaded PowerPoint template (.pptx or .potx) is processed using `python-pptx`. The app copies the template, preserving its layouts, colors, fonts, and embedded images. For each generated slide, the app selects the appropriate layout from the template and inserts the LLM-generated title and content. Images and design elements from the template are reused where possible, ensuring the final presentation matches the look and feel of the original template. No new images are generated; only those present in the template are reused.

## License
MIT
