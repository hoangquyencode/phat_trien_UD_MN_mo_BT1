# F. Gỡ lỗi:
KIỂM TRA KHI LỖI docker compose up -d





<img width="1899" height="343" alt="image" src="https://github.com/user-attachments/assets/9d37fd74-179c-407e-b810-62914ddc7624" />







version: "3.8"

services:

  myapi:
    build:
      context: ./myapi
    container_name: myapi
    ports:
      - "9630:5000"
    restart: always

    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:5000/api?tien=100"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 10s

    deploy:
      resources:
        limits:
          memory: 512M


  mynodered:
    image: nodered/node-red
    container_name: mynodered
    restart: unless-stopped
    ports:
      - "1880:1880"
    volumes:
      - ./nodered:/data
    deploy:
      resources:
        limits:
          memory: 512M


  mynginx:
    image: nginx
    container_name: mynginx
    restart: always
    ports:
      - "80:80"
    volumes:
      - ./myweb:/usr/share/nginx/html:ro
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf:ro
    deploy:
      resources:
        limits:
          memory: 256M
