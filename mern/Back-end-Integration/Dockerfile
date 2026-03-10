# ---------- Stage 1: Install dependencies ----------
FROM node:20-alpine AS builder

WORKDIR /app

# Copy package files first (for Docker cache)
COPY package*.json ./

# Install only production dependencies
RUN npm install --omit=dev

# Copy source code
COPY . .


# ---------- Stage 2: Production Image ----------
FROM node:20-alpine

WORKDIR /app

# Copy only required files from builder
COPY --from=builder /app /app

# Environment
ENV NODE_ENV=production

# Expose backend port
EXPOSE 5000

# Start app
CMD ["node", "app.js"]
