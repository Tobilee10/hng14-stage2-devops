# --- Stage 1: Build Stage ---
FROM python:3.11-slim AS builder

WORKDIR /app

COPY requirements.txt .
RUN pip install --user --no-cache-dir -r requirements.txt

# --- Stage 2: Runtime Stage ---
FROM python:3.11-slim

WORKDIR /app

# Security: Create and use a non-root user
RUN groupadd -r workergroup && useradd -r -g workergroup workeruser

# Copy installed dependencies
COPY --from=builder /root/.local /home/workeruser/.local
COPY . .

RUN chown -R workeruser:workergroup /app
USER workeruser

ENV PATH=/home/workeruser/.local/bin:$PATH

# Healthcheck: Verify the python process is running
# HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
#     CMD pgrep python || exit 1

CMD ["python", "worker.py"]