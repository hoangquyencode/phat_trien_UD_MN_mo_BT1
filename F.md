# F. Gỡ lỗi:
KIỂM TRA KHI LỖI docker compose up -d





<img width="1899" height="343" alt="image" src="https://github.com/user-attachments/assets/9d37fd74-179c-407e-b810-62914ddc7624" />







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

  deploy:
    resources:
      limits:
        memory: 512M

