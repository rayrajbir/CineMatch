# 🎬 Cine Match – AI-Powered Movie Recommendation Platform 🍿

**Cine Match** is a next-generation, full-stack movie recommendation system designed to help film enthusiasts discover their next favorite movie effortlessly.  
Built with a **Flutter mobile app**, **Django REST API**, **PostgreSQL**, and **Apache Spark**, it delivers **personalized, AI-driven recommendations** powered by large-scale data analytics.

---

## 🚀 Features

- 🔍 **Personalized Movie Recommendations** – Get curated suggestions based on your ratings, preferences, and viewing history.  
- 🎞️ **Interactive Movie Details & Ratings** – View movie info, rate them in real-time, and influence your recommendations.  
- 🎯 **User Preference Profiles** – Manage your favorite genres, watchlists, and activity insights.  
- ⚡ **AI-Powered Engine (Spark MLlib)** – Uses collaborative filtering (ALS) and content-based similarity for hybrid recommendations.  
- 📅 **Automated Daily Updates** – Spark pipeline retrains models daily via Dockerized scheduler or Airflow.  
- 📱 **Cross-Platform Mobile App** – Built in **Flutter**, optimized for Android and iOS.  
- 🐳 **Containerized Deployment** – Fully reproducible and scalable with **Docker Compose**.

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-------------|
| **Frontend (App)** | Flutter (Dart) |
| **Backend (API)** | Django + Django REST Framework |
| **Database** | PostgreSQL |
| **AI Engine** | Apache Spark MLlib (ALS Collaborative Filtering) |
| **Authentication** | JWT (SimpleJWT) |
| **DevOps / Automation** | Docker + Docker Compose + Cron / Airflow |

---

## 📁 Project Structure

```
cine-match/
├── docker-compose.yml          # Orchestrates all containers
├── backend/
│   ├── Dockerfile
│   ├── manage.py
│   ├── requirements.txt
│   ├── project/
│   │   ├── settings.py
│   │   ├── urls.py
│   ├── movies/                 # Movie, Rating models & APIs
│   ├── recommender/            # Spark job scripts & pipelines
│   ├── users/                  # Authentication & Profile logic
│   └── recommender/spark_als_job.py
├── flutter_app/
│   ├── pubspec.yaml
│   ├── lib/
│   │   ├── main.dart
│   │   ├── screens/            # Login, Home, Movie Detail, Profile
│   │   ├── providers/          # Auth & Movie state management
│   │   └── services/           # REST API communication
└── README.md
```

---

## 🧠 AI Recommendation Engine

### 🔹 Model Overview
- **Collaborative Filtering (ALS)** – Learns from user-movie rating patterns to recommend unseen titles.  
- **Hybrid Mode (optional)** – Combines content-based filtering (genre similarity via TF-IDF) with collaborative signals.  
- **Daily Refresh** – The Spark job trains a fresh model daily and stores recommendations back to PostgreSQL.

### 🔹 Pipeline Workflow
1. Extract ratings and movies from PostgreSQL.  
2. Train ALS model on Spark.  
3. Generate top-N movie recommendations for each user.  
4. Store results in `user_recommendations` table.  

Run manually:
```bash
docker-compose run --rm spark spark-submit /recommender/spark_als_job.py
```

Or schedule daily via cron:
```bash
0 2 * * * docker-compose run --rm spark spark-submit /recommender/spark_als_job.py
```

---

## ⚙️ How to Run Locally

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/yourusername/cine-match.git
cd cine-match
```

### 2️⃣ Configure Environment
Copy the environment template:
```bash
cp backend/.env.example backend/.env
```

### 3️⃣ Start Using Docker Compose
```bash
docker-compose up --build
```

This starts:
- PostgreSQL (Database)  
- Django API (Backend)  
- Spark (AI Engine)  

### 4️⃣ Apply Migrations & Create Admin
```bash
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
```

### 5️⃣ Run the Mobile App
Open `flutter_app/` and run:
```bash
flutter pub get
flutter run
```

Ensure the API URL in `lib/services/api.dart` matches your backend endpoint.

---

## 📱 Flutter UI Overview

| Screen | Description |
|--------|--------------|
| **Login / Signup** | JWT-based authentication with Django REST API |
| **Home** | Browse movies and view personalized recommendations |
| **Movie Detail** | View metadata, ratings, and similar movie suggestions |
| **Profile** | Update genre preferences and view watch history |

---

## 🧩 Example API Endpoints

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/api/movies/` | `GET` | List movies |
| `/api/movies/{id}/rate/` | `POST` | Submit or update a rating |
| `/api/user/profile/` | `GET/PUT` | Get or update preferences |
| `/api/user/recommendations/` | `GET` | Fetch top recommended movies |

---

## 🌐 Deployment

Cine Match is fully Dockerized for fast and reproducible deployment.  
You can deploy easily to:

- 🟦 **Render / Railway** – for backend API hosting  
- 🐳 **AWS ECS / EC2** – for production workloads  
- 🧠 **Databricks / Spark Cluster** – for scalable ML processing  

CI/CD with GitHub Actions and Airflow integration is planned for production automation.

---

## 👥 Team

| Name | Role |
|------|------|
| **Rajbir Ray** | Full-Stack Developer / AI Engineer |
| **—** | (Open for collaborators & contributors!) |

---

## 🤝 Contributing

We welcome contributions!  
To contribute:

```bash
git fork https://github.com/yourusername/cine-match.git
git checkout -b feat/your-feature
git commit -m "Add new feature"
git push origin feat/your-feature
```

Then open a Pull Request.

---

## 📜 License

Licensed under the **MIT License**.  
Feel free to use, modify, and build upon Cine Match with attribution.

---
