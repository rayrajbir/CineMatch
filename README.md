# 🎬 Cine Match - AI-Powered Movie Recommendations 🍿

**Cine Match** is a next-generation AI-powered movie recommendation system built to transform how film lovers discover new favorites. It uses a hybrid content-based filtering model powered by Apache Spark to generate personalized movie recommendations tailored to your unique preferences.

This innovative application is built with **Django** (backend), **PostgreSQL** (database), **Apache Spark** (AI pipeline), and **Tailwind CSS** (frontend), delivering speed, security, and a modern user experience.

---

## 🚀 Features

- 🔍 **Smart Recommendations** – Get intelligent suggestions based on genres and ratings you like.
- 🎞️ **Movie Details and Ratings** – Explore details, rate movies, and see how they rank.
- 🎯 **User Preference Profiles** – Personalize your account with genre and watchlist data.
- 🧠 **AI Recommendation Engine** – Apache Spark computes movie similarities via TF-IDF & Cosine similarity.
- 📅 **Automated Daily Updates** – Scheduled pipeline refresh using cron or Airflow.
- 📱 **Responsive UI** – Sleek design with Tailwind CSS optimized for all devices.
- 🐳 **Docker-Ready** – Full containerized deployment with Docker & Docker Compose.

---

## 🛠️ Tech Stack

| Layer        | Technology               |
|--------------|---------------------------|
| Backend      | Django + Python           |
| Database     | PostgreSQL                |
| AI Engine    | Apache Spark MLlib        |
| Frontend     | Tailwind CSS + JS         |
| DevOps       | Docker + Cron / Airflow   |

---

## 📁 Project Structure

```
cinematch/
├── docker-compose.yml
├── Dockerfile
├── manage.py
├── movies/                 # Movie models and views
├── recommendations/        # Spark logic and management commands
├── templates/             # Tailwind HTML templates
├── users/                 # Login, registration, and profile management
├── spark_pipeline.py      # AI recommendation engine
└── requirements.txt
```

---

## 🧠 AI Recommendation Engine

- Uses **TF-IDF vectorization** to encode genres, plots, and metadata.
- Applies **cosine similarity** to compute closeness between movies.
- Stores precomputed personalized recommendations per user in the `UserRecommendations` model.
- Can be extended to hybrid models including collaborative filtering.

---

## ⚙️ How to Run

### 1. Clone & Setup

```bash
git clone https://github.com/yourusername/cine-match.git
cd cine-match
cp .env.example .env
```

### 2. Using Docker (Recommended)

```bash
docker-compose up --build
```

Or run manually:

```bash
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

### 3. Run the Recommendation Engine

```bash
python manage.py run_recommender
```

To automate it:
- Add as a cron job
- Or schedule via Apache Airflow

---

## 🌐 Live Demo

🚧 **Deployment in progress**  
Expected deployment on Render / Heroku / AWS – stay tuned.

---

## ✨ Meet the Team

| Name | Role |
|------|------|
| John Doe | Project Manager |
| Jane Smith | Lead Developer |
| Alice Johnson | UI/UX Designer |

---

## 🤝 Contributing

We welcome community contributions!

To contribute:

1. Fork this repo
2. Create a feature branch: `git checkout -b feat/amazing-feature`
3. Commit your changes: `git commit -am 'Add new feature'`
4. Push to the branch: `git push origin feat/amazing-feature`
5. Create a pull request!

---

## 📘 License

Licensed under the MIT License.
