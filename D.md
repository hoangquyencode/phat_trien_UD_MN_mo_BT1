# D. (Bonus - không bắt buộc)


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







<img width="1704" height="920" alt="image" src="https://github.com/user-attachments/assets/6282aef8-a75a-4d83-9dfc-1b6db54ff981" />

