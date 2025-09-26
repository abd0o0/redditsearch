Overview
RedditSearch is a web application designed to discover and analyze near real-time trending topics, keywords, and discussions across Reddit and its subreddits. Powered by a stack of modern tools, it fetches data, processes it with AI for insights, and delivers searchable results via a user-friendly interface. Ideal for researchers, marketers, or anyone monitoring social trends, this project demonstrates full-stack development with data scraping, NLP, and web deployment.
Key Goal: Turn Reddit's vast, dynamic content into actionable intelligence—e.g., "What's trending on r/technology about AI ethics right now?"
Features

Real-Time Reddit Scraping: Pull posts, comments, and trends from subreddits using Bright Data for reliable data collection.
AI-Powered Analysis: Leverage LangChain to summarize trends, extract keywords, and generate insights (e.g., sentiment analysis).
Interactive Prototyping: Jupyter notebooks for experimenting with data pipelines and visualizations.
Web Dashboard: Django-powered frontend for searching, filtering, and visualizing results (e.g., trend graphs, topic clouds).
Customizable Queries: Search by keyword, subreddit, time frame, or engagement metrics.
Export & Alerts: Download results as CSV/JSON; optional email notifications for new trends.

Tech Stack

Backend: Django (web framework) + LangChain (AI/LLM integration for processing Reddit data).
Data Collection: Bright Data (scraping/proxies for Reddit API limits).
Prototyping & Analysis: Jupyter Notebooks (with pandas, NLTK, or matplotlib for data exploration).
Other Tools: Python 3.10+, Celery (for async tasks), PostgreSQL (DB), and optional Redis for caching.
Deployment: Docker-ready for easy setup.

Getting Started
Prerequisites

Python 3.10 or higher.
Git.
A Bright Data account (free tier available) for scraping—sign up at brightdata.com.
(Optional) OpenAI API key for LangChain (set in .env).

Installation

Clone the repository:
bashgit clone https://github.com/abd0o0/redditsearch.git
cd redditsearch

Create a virtual environment and install dependencies:
bashpython -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt

Set up environment variables (copy .env.example to .env and fill in):
textBRIGHT_DATA_API_KEY=your_bright_data_key
OPENAI_API_KEY=your_openai_key  # For LangChain
DATABASE_URL=postgresql://user:pass@localhost/redditsearch_db
DEBUG=True

Run database migrations (for Django):
bashpython manage.py migrate

Start the development server:
bashpython manage.py runserver
Open http://localhost:8000 in your browser to access the dashboard.

Usage

Prototype in Jupyter (explore data locally):
bashjupyter notebook
Open notebooks/reddit_trends_analysis.ipynb to run sample queries, e.g., fetch trends from r/news and visualize with plots.
Run a Search via Web App:

Navigate to /search on the dashboard.
Enter a keyword (e.g., "AI regulation") and subreddit (e.g., "r/futurology").
View results: Top posts, sentiment summary (via LangChain), and trend charts.


CLI Quick Search (for scripting):
bashpython search.py --query "climate change" --subreddit "r/environment" --limit 50
Outputs JSON with posts, scores, and AI-generated summary.

Check /docs for advanced configs, like custom LangChain chains or Bright Data proxy setups.
Project Structure
textredditsearch/
├── redditsearch/      # Django project root
│   ├── settings.py    # Configs (DB, APIs)
│   ├── urls.py        # Routing
│   └── wsgi.py        # Deployment entry
├── app/               # Main Django app
│   ├── views.py       # Search handlers
│   ├── models.py      # DB models (e.g., Post, Trend)
│   ├── scrapers/      # Bright Data integration
│   └── chains/        # LangChain prompts/chains for analysis
├── notebooks/         # Jupyter files
│   └── reddit_trends_analysis.ipynb  # Data exploration
├── static/            # CSS/JS for dashboard
├── templates/         # HTML templates
├── requirements.txt   # Python deps
├── .env.example       # Env template
├── manage.py          # Django management
└── README.md          # This file
Contributing
Love Reddit data? Help improve it!

Fork the repo.
Create a branch (git checkout -b feature/new-scraper).
Commit changes (git commit -m "Add subreddit filter").
Push and open a PR.

Follow PEP 8 style. See CONTRIBUTING.md for guidelines.
License
This project is licensed under the MIT License—see LICENSE for details.
Acknowledgments

Built with inspiration from LangChain docs and Reddit's API guidelines.
Shoutout to Bright Data for robust scraping tools.
