# Use a lightweight Python image
FROM python:3.12-slim

# Set environment variables
ENV PYTHONUNBUFFERED=1 

# Set the working directory
WORKDIR /app

# Copy only requirements.txt first (for caching)
COPY requirements.txt .

# Install dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends python3-pip && \
    pip install --no-cache-dir -r requirements.txt && \
    rm -rf /var/lib/apt/lists/*

# Copy the rest of the application
COPY . .

# Expose the port (optional, for clarity)
EXPOSE 8000

# Define the entrypoint and command properly
ENTRYPOINT ["python3", "manage.py"]
CMD ["runserver", "0.0.0.0:8000"]

