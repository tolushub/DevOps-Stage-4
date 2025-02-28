FROM python:3.6-slim
WORKDIR /app

# Install build dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    gcc \
    libc-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .
ENV REDIS_HOST=redis-queue
ENV REDIS_PORT=6379
ENV REDIS_CHANNEL=log_channel
CMD ["python", "log_processor.py"]