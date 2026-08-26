FROM python:3.10-slim

WORKDIR /app

# Install build essentials and pipenv
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/* \
    && pip install --no-cache-dir pipenv

# Copy Pipfile and Pipfile.lock
COPY Pipfile Pipfile.lock* ./

# Install dependencies into system Python
RUN pipenv install --system --deploy || pipenv install --system --skip-lock

# Copy application source
COPY . .

EXPOSE 5000

CMD ["python", "app.py"]