FROM python:3.11-bullseye

# Open port 7860 for http service
ENV FAST_API_PORT=7860
EXPOSE 7860

# Install system dependencies for OpenCV
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libgomp1 \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY *.py .
COPY index.html index.html
COPY ./requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

# Start the FastAPI server, binding to 0.0.0.0 instead of localhost
CMD python3 server.py --host 0.0.0.0 --port ${FAST_API_PORT}