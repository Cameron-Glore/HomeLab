# n8n Daily News Automation Lab

## Overview

This lab demonstrates a workflow automation built using n8n that collects news articles from multiple RSS feeds and delivers them automatically to a private Discord server each morning.

The workflow runs on a daily schedule, retrieves articles from multiple RSS sources, limits the number of articles retrieved from each feed, merges the results, and sends the final output to Discord.

The automation is hosted on a VPS provided by Hostinger using their n8n deployment environment.

---

## Architecture
Daily Schedule Trigger
↓
4 RSS Feed Sources
↓
Limit Node (2 stories each)
↓
Merge Node
↓
Discord Message
↓
Private Discord Server

---

## Environment

| Component | Description |
|---|---|
| Automation Platform | n8n |
| Hosting Provider | Hostinger |
| Messaging Platform | Discord |
| Trigger | Scheduled automation |

---

## Step 1 — Daily Trigger

A Schedule Trigger node runs the workflow automatically each morning.

Configuration:

- Trigger Type: Schedule
- Frequency: Daily
- Execution Time: Morning

Purpose:

- automate workflow execution
- provide a consistent daily news briefing
- eliminate manual runs

---

## Step 2 — RSS Feed Collection

Four RSS feed nodes retrieve news articles from selected sources.

Each RSS feed returns structured data including:

- title
- author
- snippet
- article link

---

## Step 3 — Limit Articles

Each RSS feed connects to its own Limit node.

Configuration:

Limit: **2 articles per feed**

Total possible output:

4 feeds × 2 articles = **8 stories per day**

This prevents excessive message output.

---

## Step 4 — Merge Feeds

All limited feeds are combined using the **Merge node**.

The Merge node aggregates the articles into a single stream before delivery.

Purpose:

- combine multiple data sources
- simplify output
- create a unified news feed

---

## Step 5 — Discord Delivery

The merged article stream connects to a Discord node.

The Discord node sends the formatted article information to a private Discord server created for this automation.

Each message contains:

- Author
- Title
- Content snippet
- Article link

---

## Step 6 — Hosting

The automation runs on a cloud-hosted environment using Hostinger's n8n deployment.

This allows the workflow to operate continuously without relying on a local machine.

---

## Workflow Summary

The completed automation performs the following tasks:

1. Runs automatically each morning
2. Retrieves articles from four RSS feeds
3. Limits each feed to two stories
4. Merges the results into one stream
5. Sends the news feed to a Discord server

---

## Skills Demonstrated

This lab demonstrates:

- workflow automation
- scheduled task execution
- RSS data ingestion
- data aggregation
- merge logic
- messaging integration
- cloud-hosted automation

---

## Future Improvements

Planned improvements include:

- AI-powered article summarization
- duplicate article filtering
- topic categorization
- email delivery option
- additional automation workflows
