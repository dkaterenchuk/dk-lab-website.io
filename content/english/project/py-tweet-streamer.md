---
title: "py_tweet_streamer: Twitter Data Collection"
description: "Twitter streaming library based on tweepy API for real-time tweet collection"
draft: false
image : "images/projects/py_tweet_streamer.jpg"
bg_image: "images/projects/py_tweetstreamer-bg.png"
category: ["Data Collection", "Social Media", "Python"]
weight: 5
information:
  - label : "Project Type"
    info : "Open Source Tool"
  - label : "Domain"
    info : "Social Media Analytics"
  - label : "Technologies"
    info : "Python, Tweepy, Twitter API"
  - label : "GitHub"
    info : "https://github.com/dkaterenchuk/py_tweet_streamer"
  - label : "Stars"
    info : "2"  # Updated stars count
  - label : "License"
    info : "MIT"
---

## py_tweet_streamer: Twitter Data Collection

A Python-based Twitter streaming application that captures tweets in real-time using the Tweepy API, designed for researchers and analysts who need to collect social media data continuously.

### Overview

This tool enables continuous collection of Twitter data based on search terms, with built-in fault tolerance and efficient storage. It's ideal for social media research, sentiment analysis, trend tracking, and other applications requiring real-time Twitter data collection.

### Key Features

- **Real-time streaming** - Captures tweets matching specified search terms as they happen
- **Chunked storage** - Organizes collected data into daily files for easy management
- **Resilient operation** - Designed to run continuously without interruption
- **Fault tolerance** - Recovers gracefully from network issues or API disruptions
- **Data preservation** - Stores complete tweet information including metadata, location, and retweet data
- **Rate limiting** - Built-in rate limit protection (one request every three seconds)
- **Compressed storage** - Uses gzip compression to optimize disk space

### Installation & Setup

**Dependencies:**

```bash
pip install tweepy
```

**Twitter API Credentials:**

You'll need to obtain Twitter API credentials from Twitter's developer portal. Create a `TOKENS.txt` file based on the provided `TOKENS.txt.example` template.

**Security recommendation:**

```bash
chmod 400 TOKENS.txt  # On Linux/Mac systems
```

### Usage

Basic command structure:

```bash
python tweet_streamer.py <output_folder> <search_term1> [search_term2] [...]
```

**Example - Collect election news:**

```bash
python tweet_streamer.py my_data/ news usa election
```

This will continuously collect tweets matching the terms "news", "usa", and "election", storing them in the `my_data/` folder.

### Data Management

- **Storage format**: Gzip-compressed JSON files
- **File organization**: Daily files for optimal memory usage and portability
- **Data access**: Includes `tweet_data_reader.py` as a reference implementation for parsing collected data
- **Control**: Press Ctrl+C twice to stop streaming

### Research Applications

- **Sentiment analysis** - Track public opinion on topics or events
- **Trend analysis** - Monitor emerging trends and hashtags
- **Social network analysis** - Study information diffusion and user interactions
- **Event tracking** - Collect data during specific events or time periods
- **Content analysis** - Study linguistic patterns and discourse

### Resources

- **GitHub Repository**: [py_tweet_streamer](https://github.com/dkaterenchuk/py_tweet_streamer)
- **License**: MIT
- **API Backend**: Twitter API via Tweepy

This tool provides researchers with a reliable way to collect Twitter data for analysis, enabling studies in social media dynamics, public opinion, and online communication patterns.
