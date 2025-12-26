FROM python:3.9-slim

WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y gcc libpq-dev && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
# Increase timeout because torch is huge
RUN pip install --no-cache-dir \
    --extra-index-url https://download.pytorch.org/whl/cpu \
    -r requirements.txt \
    --timeout 300


COPY . .

# --- ADD THIS LINE ---
ENV PYTHONUNBUFFERED=1

CMD ["python", "worker.py"]