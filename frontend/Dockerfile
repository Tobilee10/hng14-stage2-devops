# --- Stage 1: Build Stage ---
FROM node:18-alpine AS builder

WORKDIR /app

COPY package*.json ./
# Use 'npm ci' for predictable, clean installs in CI/CD
RUN npm ci --only=production

# --- Stage 2: Runtime Stage ---
FROM node:18-alpine

WORKDIR /app

# Copy node_modules from builder and the rest of the source
COPY --from=builder /app/node_modules ./node_modules
COPY . .

# Security: Use the built-in 'node' user
USER node

EXPOSE 3000

# Healthcheck using wget (standard in Alpine)
# HEALTHCHECK --interval=30s --timeout=10s --retries=3 \
#     CMD wget --no-verbose --tries=1 --spider http://localhost:3000/ || exit 1

CMD ["node", "app.js"]