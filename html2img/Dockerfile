FROM node:20-slim

RUN apt-get update && apt-get install -y \
    chromium \
    fonts-noto-color-emoji \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

# Add Cairo Arabic font
RUN apt-get update && apt-get install -y fonts-cairo --no-install-recommends && rm -rf /var/lib/apt/lists/*

ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium
ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true

WORKDIR /app
COPY package.json server.js ./
RUN npm install --production

EXPOSE 3100
CMD ["node", "server.js"]
