Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421
Lớp: 58KTPM

Bài tập 01:

deadline : 23h59 ngày 13 tháng 4 năm 2026.

A. Đăng ký tên miền xịn cho cá nhân
1. Đăng ký domain






<img width="1891" height="945" alt="image" src="https://github.com/user-attachments/assets/ee9154e1-31df-4e2e-99b9-0734760b8812" />





2. Đăng ký tài khoản cloudflare



<img width="1277" height="562" alt="image" src="https://github.com/user-attachments/assets/a0b4fe06-de03-4f28-bbc5-fb63a57bb985" />






<img width="1148" height="882" alt="image" src="https://github.com/user-attachments/assets/24ba7468-247f-4400-ac1e-d9c32733d313" />







B. Cài đặt Ubuntu + Docker
Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
Sử dụng công cụ để giả lập: HyperV (có sẵn của windows)
Vào Windows Features -> tích chọn Hyper_V như hình:





<img width="602" height="862" alt="image" src="https://github.com/user-attachments/assets/2960d050-1e4c-4de3-8ef7-0f1d1584db3f" />






Download file iso để cài đặt.




<img width="1170" height="189" alt="image" src="https://github.com/user-attachments/assets/a39f3a52-57f8-4db6-93e7-84594c689e79" />







Vào Hyper-V Manager -> chọn Virtual Swich manager... để tạo máy ảo MyUbuntu






<img width="1179" height="818" alt="image" src="https://github.com/user-attachments/assets/321bc09d-f6a9-4f0c-9a3c-0d03c1ff2dcb" />







Start -> Conect máy ảo -> thiết lập cài đặt






<img width="1275" height="1023" alt="image" src="https://github.com/user-attachments/assets/63a5efd2-dfff-4b56-9c0e-3ac4c26024e3" />








<img width="1296" height="1030" alt="image" src="https://github.com/user-attachments/assets/faa6e417-5276-4e6d-a45f-d695f9a6d5c5" />







CÀI SSH SERVER
sudo apt update
sudo apt install openssh-server -y







<img width="976" height="902" alt="image" src="https://github.com/user-attachments/assets/ef67743b-e160-4c8a-b11f-8267bcfe23bb" />






Địa chỉ IP để bạn kết nối từ máy tính khác vào máy ảo này là:
192.168.1.147







<img width="963" height="578" alt="image" src="https://github.com/user-attachments/assets/b3a0274b-4af1-4ff3-b8d4-dcd2a61e27fa" />







Windows → SSH → Ubuntu
ssh hoangquyen@192.168.1.147






<img width="952" height="620" alt="image" src="https://github.com/user-attachments/assets/ddc29c49-d08f-4b18-bf2c-b9b9362c60f4" />






Cài docker bằng lệnh 
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
docker run hello-world
sudo apt install docker-compose-v2 -y
docker compose version









<img width="1087" height="628" alt="image" src="https://github.com/user-attachments/assets/4cca7adb-0b7b-4d6c-a400-35cb7c8f418d" />






Tạo các file 


myapp/
│
├── docker-compose.yml
├── Dockerfile   
├── requirements.txt
│
├── myapi/
│   ├── app.py
│   ├── templates/
│   │   └── index.html   (nếu dùng Flask render)
│   
└── README.md


tạo file index.html và thả code vào





<img width="893" height="152" alt="image" src="https://github.com/user-attachments/assets/4ae9ffee-fe53-4783-b743-86aa2d2a19c6" />










































