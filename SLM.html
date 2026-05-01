from flask import Flask, request, jsonify
import sqlite3
from flask_cors import CORS

app = Flask(__name__)
CORS(app)

# ---------- DATABASE CONNECTION ----------
def get_db():
    conn = sqlite3.connect('database.db')
    conn.row_factory = sqlite3.Row
    return conn

# ---------- CREATE TABLES ----------
def init_db():
    conn = get_db()
    cur = conn.cursor()

    cur.execute('''
    CREATE TABLE IF NOT EXISTS users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT,
        email TEXT UNIQUE,
        password TEXT
    )
    ''')

    cur.execute('''
    CREATE TABLE IF NOT EXISTS workers (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT,
        type TEXT,
        phone TEXT
    )
    ''')

    cur.execute('''
    CREATE TABLE IF NOT EXISTS bookings (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        user_email TEXT,
        worker_name TEXT,
        date TEXT
    )
    ''')

    conn.commit()
    conn.close()

init_db()

# ---------- SIGNUP ----------
@app.route('/signup', methods=['POST'])
def signup():
    data = request.json
    name = data.get('name')
    email = data.get('email')
    password = data.get('password')

    if not name or not email or not password:
        return jsonify({"message": "All fields required"})

    try:
        conn = get_db()
        cur = conn.cursor()

        cur.execute("INSERT INTO users (name, email, password) VALUES (?, ?, ?)",
                    (name, email, password))

        conn.commit()
        conn.close()

        return jsonify({"message": "Signup successful"})
    except:
        return jsonify({"message": "User already exists"})

# ---------- LOGIN ----------
@app.route('/login', methods=['POST'])
def login():
    data = request.json
    email = data.get('email')
    password = data.get('password')

    conn = get_db()
    cur = conn.cursor()

    cur.execute("SELECT * FROM users WHERE email=? AND password=?",
                (email, password))
    user = cur.fetchone()

    conn.close()

    if user:
        return jsonify({"message": "Login successful"})
    else:
        return jsonify({"message": "Invalid email or password"})

# ---------- ADD WORKER ----------
@app.route('/add_worker', methods=['POST'])
def add_worker():
    data = request.json
    name = data.get('name')
    w_type = data.get('type')
    phone = data.get('phone')

    if not name or not w_type or not phone:
        return jsonify({"message": "All fields required"})

    conn = get_db()
    cur = conn.cursor()

    cur.execute("INSERT INTO workers (name, type, phone) VALUES (?, ?, ?)",
                (name, w_type, phone))

    conn.commit()
    conn.close()

    return jsonify({"message": "Worker added successfully"})

# ---------- GET WORKERS ----------
@app.route('/workers', methods=['GET'])
def get_workers():
    conn = get_db()
    cur = conn.cursor()

    cur.execute("SELECT * FROM workers")
    rows = cur.fetchall()

    workers = []
    for row in rows:
        workers.append({
            "id": row["id"],
            "name": row["name"],
            "type": row["type"],
            "phone": row["phone"]
        })

    conn.close()

    return jsonify(workers)

# ---------- BOOK SERVICE ----------
@app.route('/book', methods=['POST'])
def book():
    data = request.json
    email = data.get('email')
    worker = data.get('worker')
    date = data.get('date')

    if not email or not worker or not date:
        return jsonify({"message": "All fields required"})

    conn = get_db()
    cur = conn.cursor()

    cur.execute("INSERT INTO bookings (user_email, worker_name, date) VALUES (?, ?, ?)",
                (email, worker, date))

    conn.commit()
    conn.close()

    return jsonify({"message": "Booking successful"})

# ---------- GET BOOKINGS ----------
@app.route('/bookings', methods=['GET'])
def get_bookings():
    conn = get_db()
    cur = conn.cursor()

    cur.execute("SELECT * FROM bookings")
    rows = cur.fetchall()

    bookings = []
    for row in rows:
        bookings.append({
            "id": row["id"],
            "user_email": row["user_email"],
            "worker_name": row["worker_name"],
            "date": row["date"]
        })

    conn.close()

    return jsonify(bookings)

# ---------- RUN ----------
if __name__ == '__main__':
    app.run(debug=True)
