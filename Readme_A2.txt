================================================================================
COSC 2671 — Social Media and Network Analytics
Assignment 2 — Group Project
================================================================================

Project Title : Narrative Tribes: Mapping Influence, Sentiment, and Community
               Dynamics in AI Discourse on GitHub
Team Members  : Hritesh Ray (s4134744) · Abhijeet Ghadge (s4135096)
Group         : PG Group 24
Anchor Event  : DeepSeek R1 Release — January 20, 2025
Data Source   : GitHub REST API (api.github.com)

================================================================================
SUBMITTED FILES
================================================================================

1. Report_s4134744_PG_Group24.pdf
   Final project report 

2. s4134744_PG_Group24.ipynb
   Jupyter notebook containing all data collection, network analysis,
   NLP analysis, and visualisation code

3. README.txt
   This file

4. Worksheet_s4134744_PG_Group24.pdf
   Team project plan, weekly timesheets, and individual self-reflections

5. data/
   Collected data 
   - gh_api_full.csv(Full dataset): (3,732 events)
   - centrality_scores.csv        : Full centrality + role classifications (842 users)
   - topic_info.csv               : BERTopic topic information (15 topics)

================================================================================
NOTE ON FULL DATASET
================================================================================

The full dataset includes:
  - 3,732 GitHub events across 3 repositories
  - 1,540 unique users
  - Date range: January 13 – February 2, 2025
  - Fields: event_type, repo, actor, created_at, text, in_reply_to, issue_number

================================================================================
HOW TO RUN THE NOTEBOOK
================================================================================

PREREQUISITES
-------------
Python       : 3.9 or higher (tested on 3.13.5, Anaconda)
Jupyter      : Notebook or JupyterLab

INSTALLATION
------------
All required packages are installed in Cell 0 (Environment Setup).
Run Cell 0 first — it installs all dependencies automatically.

Key packages installed:
  requests, python-dotenv, pandas, numpy, networkx, python-louvain,
  leidenalg, igraph, vaderSentiment, transformers, bertopic,
  sentence-transformers, matplotlib, seaborn, plotly, scipy, tqdm

AUTHENTICATION (GitHub API)
---------------------------
Cell 3 (Full Data Collection) uses the GitHub REST API.
To reproduce the data collection:

  1. Create a Personal Access Token (PAT) at https://github.com/settings/tokens
     Required scope: public_repo (read-only)
  2. Create a file named .env in the same directory as the notebook
  3. Add the following line to .env:
        GITHUB_TOKEN=personal_access_token_here


NOTE: A PAT is optional — the API is publicly accessible without one,
but rate-limited to 60 requests/hour (vs 5,000 with a PAT).
Data collection without a PAT will take approximately 90 minutes.
The data sample is provided so markers do not need to re-collect.

================================================================================
CELL EXECUTION ORDER
================================================================================

Run cells in the following order.

Cell 0  — Environment Setup
Cell 1  — Pilot Test & Dataset Feasibility
Cell 2  — Network Design Validation (Pilot)
Cell 3  — Full Data Collection (GitHub REST API)
Cell 4  — Data Validation
Cell 5  — Network Construction
Cell 6  — Centrality Analysis
Cell 7  — Community Detection
Cell 8  — Role Classification
Cell 9  — Network Visualisation
Cell 10 — Topic Modelling (BERTopic)
Cell 11 — Sentiment Analysis (Supplementary)
Cell 12 — Topic Visualisations
Cell 13 — Final Results Summary
================================================================================
EXPECTED OUTPUT FILES
================================================================================

data/
  gh_pilot.csv                  Pilot dataset (2-day, 382 events)
  gh_api_full.csv               Full dataset (3,732 events)
  centrality_scores.csv         Centrality + community + role (842 users)
  text_with_topics.csv          Text with topic labels + sentiment scores
  topic_info.csv                BERTopic topic information

outputs/
  network_layer1.png            Co-participation network (top 200 users)
  topic_evolution.png           Topic evolution pre/during/post release
  topic_community_heatmap.png   Topic x community heatmap
  sentiment_timeline.png        Daily sentiment by community
  fig_a1_event_volume.png       Event volume per repo per period
  fig_a2_event_types.png        Event type breakdown per repo
  fig_a3_daily_timeline.png     Daily activity timeline
  fig_b1_degree_distribution.png  Degree distribution (log-log)
  fig_b2_community_sizes.png    Community size distribution
  fig_b3_role_distribution.png  Role distribution (pie + stacked bar)
  fig_b4_top10_pagerank.png     Top 10 users by PageRank
  fig_b5_algorithm_comparison.png  Louvain vs Leiden comparison
  fig_c1_topic_sizes.png        BERTopic topic sizes
  fig_c2_sentiment_distribution.png  Sentiment per period
  fig_c3_sentiment_boxplot.png  Sentiment by community (box plot)

