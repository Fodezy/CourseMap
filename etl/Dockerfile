# Use official slim Python 3.11 image
FROM python:3.11-slim

# set working directory
WORKDIR /app

# install OS‑level dependencies (add others as needed, e.g. tesseract, ghostscript)
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      gcc \
      libpq-dev \
 && rm -rf /var/lib/apt/lists/*

# copy and install Python dependencies
COPY requirements.txt .
RUN pip install --upgrade pip \
 && pip install --no-cache-dir -r requirements.txt

# copy application code
COPY . .

# expose the FastAPI port
EXPOSE 8000

# default command: run Uvicorn
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
