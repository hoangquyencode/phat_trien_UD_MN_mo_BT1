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
│   │
│   └── templates/
│       └── index.html   (Flask render HTML nếu dùng)
│
└── README.md



tạo file index.html và thả code vào





<img width="893" height="152" alt="image" src="https://github.com/user-attachments/assets/4ae9ffee-fe53-4783-b743-86aa2d2a19c6" />






# Dockerfile:

FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

CMD ["python", "app.py"]


# requirements.txt
flask

# app.py

app = Flask(__name__)

@app.route('/api', methods=['GET'])
def tinh_vat():
    tien = request.args.get('tien')

    # kiểm tra input
    if not tien:
        return jsonify({"error": "Vui lòng nhập số tiền"}), 400

    try:
        tien = float(tien)
        vat = tien * 0.1
        tong = tien + vat

        return jsonify({
            "so_tien_goc": tien,
            "thue_vat": "10%",
            "tong_cong": tong
        })

# index.html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Web Bộ đội tí hon</title>

    <style>
        body, html {
            height: 100%;
            margin: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: white;
            text-align: center;
        }

        .container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 20px;
            animation: glow 2s infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 0 0 10px #fff; }
            to { text-shadow: 0 0 20px #ff0; }
        }

        input {
            padding: 10px;
            font-size: 18px;
            width: 200px;
            border-radius: 5px;
            border: none;
        }

        button {
            padding: 10px 20px;
            font-size: 18px;
            margin-left: 10px;
            border: none;
            border-radius: 5px;
            background: #ff9800;
            color: white;
            cursor: pointer;
        }

        button:hover {
            background: #e68900;
        }

        .result {
            margin-top: 20px;
            font-size: 1.5rem;
        }
    </style>
</head>

<body>

<div class="container">
    <h1>🎖 Bộ đội tí hon 🎖</h1>

    <p>Nhập số tiền để tính VAT 10%</p>

    <input type="number" id="tien" placeholder="Nhập tiền...">
    <button onclick="tinhVAT()">Tính</button>

    <div class="result" id="ketqua"></div>
</div>

<script>
function tinhVAT() {
    let tien = document.getElementById("tien").value;

    if (!tien) {
        alert("Nhập số tiền!");
        return;
    }

    fetch(`/api?tien=${tien}`)
        .then(res => res.json())
        .then(data => {
            if (data.error) {
                document.getElementById("ketqua").innerHTML = "❌ " + data.error;
            } else {
                document.getElementById("ketqua").innerHTML =
                    `💰 Gốc: ${data.so_tien_goc} <br>
                     📊 VAT: ${data.thue_vat} <br>
                     ✅ Tổng: ${data.tong_cong}`;
            }
        })
        .catch(err => {
            document.getElementById("ketqua").innerHTML = "Lỗi kết nối API!";
        });
}
</script>

</body>
</html>






<img width="910" height="246" alt="image" src="https://github.com/user-attachments/assets/79892cb9-47aa-4319-a63f-acec47f76389" />









<img width="1877" height="1053" alt="image" src="https://github.com/user-attachments/assets/3b00338e-1394-4614-833c-447f162b9aae" />


















