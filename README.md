# 👤 Face Detection Service - Mind Sync Smart Glasses

This repository contains the Node.js-based face recognition microservice used in the **Mind Sync Smart Glasses** project. It performs real-time face detection and matching using `face-api.js` and enables AI memory recall to associate events with known people.

---

## 👨‍💻 Developer Responsibility

**Service Type:** Backend Microservice
**Technology:** Node.js + TensorFlow\.js (face-api.js)

---

## 🎯 Objective

To extract face embeddings from captured images, compare them with stored vectors, and return identity matches to the embedding backend.

---

## ⚙️ Tech Stack

* Node.js
* Express.js
* Multer (image upload middleware)
* face-api.js (TensorFlow\.js-based face detection)
* MongoDB (store face data)

---

## 📁 Project Structure

```
FaceDetection/
├── models/              # face-api.js pre-trained models
├── index.js             # Server entry point
└── .env                 # Environment variables
```

---

## 🛠️ Setup Instructions

```bash
git clone https://github.com/Mahesh-656/Face_Detection.git
cd FaceDetection
npm install
```

Create a `.env` file:

```env
PORT=5001
MONGO_URI=your-mongodb-uri
```

Start the server:

```bash
node index.js
```

---

## 🔌 API Endpoints

### `POST /upload`

* Accepts: multipart image
* Action: Extracts face vector embedding
* Response:

```json
{
  "embedding": [0.032, -0.017, ..., 0.041]
}
```

### `POST /match-face`

* Accepts: `{ "embedding": [vector] }`
* Action: Compares with known users
* Response:

```json
{
  "match": "Maheshwar",
  "score": 0.91,
  "success": true
}
```

---

## 📥 Model Setup

Download the following face-api models and place them in `public/models/`:

* `face_landmark_68_model`
* `face_recognition_model`
* `ssd_mobilenetv1`

---

## ✅ Match Criteria

* Cosine similarity score ≥ 0.9 is considered a valid face match.
* Supports multiple known users.

---

## 📊 Example Use Case

ESP32\_CAM uploads an image ➝ This service extracts face ➝ EmbeddingServices tags the event with the matched person ➝ Frontend displays summary to the user.

---

## 👨‍🎓 Project Info

**Final Year Project**,
**Title:** Mind Sync Smart Glasses,
**Component:** Face Detection Microservice

---

