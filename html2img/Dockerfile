FROM node:20-slim

RUN apt-get update && apt-get install -y \
    chromium \
    fonts-noto-color-emoji \
    fonts-noto-cjk \
    fonts-freefont-ttf \
    wget \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

# Download Cairo Arabic font from Google Fonts
RUN mkdir -p /usr/share/fonts/cairo && \
    wget -q -O /usr/share/fonts/cairo/Cairo-Variable.ttf "https://github.com/google/fonts/raw/main/ofl/cairo/Cairo%5Bslnt%2Cwght%5D.ttf" && \
    fc-cache -f -v 2>/dev/null || true

ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium
ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true

WORKDIR /app
COPY package.json server.js ./
RUN npm install --production

EXPOSE 3200
CMD ["node", "server.js"]
