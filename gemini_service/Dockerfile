# Use official Python base image
FROM python:3.9

# Install tesseract + ffmpeg for OCR and audio conversion
RUN apt-get update && apt-get install -y \
    tesseract-ocr \
    ffmpeg  # ✅ this is needed by pydub

# Set the working directory inside the container
WORKDIR /app

# Copy all project files into the container
COPY . .

# Install required Python packages
RUN pip install --no-cache-dir \
    fastapi uvicorn httpx python-dotenv pillow pytesseract \
    speechrecognition python-multipart pymongo \
    google-generativeai pydub

# Add the current path to Python module path
ENV PYTHONPATH=/app

# Expose the port FastAPI will run on
EXPOSE 8002

# Start the FastAPI app
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8002"]