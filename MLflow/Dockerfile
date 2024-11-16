# Base image
FROM python:3.10

# Install necessary Python packages
RUN pip install mlflow

# Set working directory
WORKDIR /app

# Copy application files (if any)
COPY . /app

# Run mlflow server
ENTRYPOINT ["mlflow", "server", "-h", "0.0.0.0"]
