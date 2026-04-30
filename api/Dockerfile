# --- Stage 1: Build Stage ---
FROM python:3.11-slim AS builder

WORKDIR /app

# Install build-essential for any C-based python extensions
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    python3-dev \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
# Install dependencies to a local folder to copy easily
RUN pip install --user --no-cache-dir -r requirements.txt

# --- Stage 2: Runtime Stage ---
FROM python:3.11-slim

WORKDIR /app

# Install curl for the HEALTHCHECK instruction
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Security: Create and use a non-root user
RUN groupadd -r apiuser && useradd -r -g apiuser apiuser

# Copy only the necessary library files from the builder
COPY --from=builder /root/.local /home/apiuser/.local
COPY . .

# Ensure the app user owns the application files
RUN chown -R apiuser:apiuser /app
USER apiuser

# Add the local bin to PATH so uvicorn can be found
ENV PATH=/home/apiuser/.local/bin:$PATH

EXPOSE 8000

# HEALTHCHECK --interval=30s --timeout=5s --start-period=15s --retries=3 \
#     CMD curl -f http://localhost:8000/health || exit 1

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"] 