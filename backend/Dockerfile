FROM node:20-alpine

ENV NODE_ENV=production
WORKDIR /app

# Install dependencies first (better layer caching)
COPY package*.json ./
RUN npm ci --omit=dev

# Copy the rest of the API source
COPY . .

# Render injects PORT at runtime; server.js reads process.env.PORT (default 5000)
EXPOSE 5000

USER node
CMD ["node", "server.js"]
