FROM node:16-bullseye

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

EXPOSE 3401

# vue-cli dev server; bind to 0.0.0.0 so it's reachable from outside the container.
# VUE_APP_BACKEND_URL is injected via compose env and overrides .env.development
# (vue-cli's dotenv does not override pre-existing env vars).
CMD ["npx", "vue-cli-service", "serve", "--host", "0.0.0.0", "--port", "3401"]
