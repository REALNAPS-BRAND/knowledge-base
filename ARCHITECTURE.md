# Realnaps: Distributed System Overview

## 1.0 Introduction

This document provides a high-level overview of the Realnaps distributed system architecture. Its purpose is to explain how the different component repositories and services work together to deliver real-time virtual betting predictions and automated bet placement services. This is a foundational guide for any developer or product team member involved in the Realnaps ecosystem.

## 2.0 Architectural Philosophy

The Realnaps system is designed as a set of decoupled, specialized services that communicate through APIs and webhooks. This microservice-style architecture ensures:

- **Separation of Concerns**: Each component has one primary responsibility (e.g., scraping, routing, prediction, user interface).
- **Scalability**: Individual components can be scaled independently based on load.
- **Resilience**: A failure in one component (e.g., the scraper) does not necessarily bring down the entire system.
- **Maintainability**: Smaller, focused codebases are easier to understand, maintain, and update.

## 3.0 System Components & Repositories

The Realnaps ecosystem is composed of the following core components, each corresponding to a repository in the realnaps-brand GitHub organization.

### 3.1 realnaps-bet-data-scrapper

- **Responsibility**: This is the data origination service. Its sole purpose is to gather raw data (upcoming fixtures and past results) from third-party virtual football betting sites.
- **Technology**: Node.js, Puppeteer (for browser automation and scraping)
- **Input**: The system is custom-built for each betting site and fed with a URL, XPaths, and custom workflows to extract specific data like match fixtures with timestamps, teams, odds, and results.
- **Output**: Structured JSON data containing fixture details or game results, sent to the realnaps-data-scrapped-router.

### 3.2 realnaps-data-scrapped-router

- **Responsibility**: Acts as a simple, stateless data router and entry point into our internal processing system. It receives raw data from the scraper and routes it to the correct service (initially the external n8n webhook for prediction, and the main server for results).
- **Technology**: Lightweight Node.js server (e.g., Express.js)
- **Input**: JSON payloads from the realnaps-bet-data-scrapper
- **Output**: HTTP requests forwarding the JSON data to either the n8n Prediction Webhook or the realnaps-server

### 3.3 n8n Prediction Engine (External Service)

- **Responsibility**: This is the core logic and "brain" of the prediction system. It is an external n8n instance with a webhook exposed to us. It receives fixture data, applies predictive models, and logs historical performance for model improvement.
- **Technology**: n8n (Workflow Automation Tool)
- **Input**: Fixture data received via its webhook from our realnaps-data-scrapped-router
- **Output**: A JSON object containing the original fixture data enriched with a prediction, sent back to a specified endpoint on our realnaps-server

### 3.4 realnaps-server

- **Responsibility**: The primary API and data persistence layer for all Realnaps products. It manages user accounts, subscriptions, and stores all official predictions and results. It is the single source of truth for the client applications.
- **Technology**: Web API framework (Node.js/Express), SQL (MySQL)
- **Input**: Processed predictions from the n8n Prediction Engine, result data from the realnaps-data-scrapped-router, and user requests from clients
- **Output**: JSON data served to the realnaps-web-client and realnaps-desktop-client

### 3.5 realnaps-web-client (Prediction Bot)

- **Responsibility**: The user-facing web application that displays real-time predictions to subscribers. It handles user authentication and presents the data served by realnaps-server.
- **Technology**: Modern PHP OOP
- **Input**: User interactions (login, etc.), real-time data from the realnaps-server API
- **Output**: A rendered web interface for users

### 3.6 realnaps-desktop-client (Outcome Placer)

- **Responsibility**: The desktop application that provides bet automation capabilities. It authenticates with the realnaps-server to validate user subscriptions and can be configured by the user to execute strategies.
- **Technology**: Desktop application framework (Electron)
- **Input**: User-defined strategies and limits, data from realnaps-server
- **Output**: Automated interactions with third-party betting websites using Puppeteer

## 4.0 Core Data Flows

### 4.1 Prediction Generation Flow

1. **Scrape**: `realnaps-bet-data-scrapper` scrapes a new set of fixtures and sends the JSON data to the `realnaps-data-scrapped-router`

2. **Route to n8n**: The router receives the fixture data and immediately forwards it to the external n8n Prediction Webhook

3. **Predict**: The external n8n Workflow receives the fixtures, runs its prediction models, and checks its internal state to prevent duplicate predictions

4. **Log to Server**: n8n sends the final prediction (fixture data + prediction) directly to a specific endpoint on the `realnaps-server`

5. **Persist & Display**: The `realnaps-server` saves the prediction to its database. The `realnaps-web-client`, which is connected to the server, receives the new prediction and displays it to the user in real-time

### 4.2 Result Logging Flow

1. **Scrape**: `realnaps-bet-data-scrapper` scrapes the results of a completed game and sends the JSON to the `realnaps-data-scrapped-router`

2. **Route to Server & n8n**: The router forks the result data, sending it simultaneously to:
   - **To n8n**: For internal logging, model performance evaluation, and historical data analysis to improve future predictions
   - **To realnaps-server**: For result storage, performance tracking, and user statistics

3. **Model Learning**: n8n receives the result data and compares it against its previous predictions to calculate accuracy metrics and update its predictive models

4. **Database Update**: The `realnaps-server` stores the results in the database and updates prediction accuracy statistics

5. **Performance Analytics**: The server calculates win/loss ratios, prediction accuracy rates, and other performance metrics that are displayed to users via the `realnaps-web-client`

## 5.0 System Integration Points

### 5.1 Authentication & Authorization
- All client applications authenticate through the `realnaps-server`
- Subscription validation occurs at the server level before serving predictions or allowing desktop client functionality
- API endpoints are secured with appropriate authentication tokens

### 5.2 Real-time Communication
- The `realnaps-web-client` maintains persistent connections to the `realnaps-server` for real-time prediction updates
- Webhooks are used for inter-service communication to ensure immediate data propagation
- The system supports high-frequency updates during peak betting periods

### 5.3 Error Handling & Monitoring
- Each component implements comprehensive error logging and reporting
- Failed predictions or scraping attempts are logged and can trigger alerts
- The system maintains operational metrics for monitoring service health and performance

## 6.0 Deployment Architecture

The Realnaps system is designed to be deployed across multiple environments with each component independently deployable and scalable. This allows for:

- **Development Environment**: Full system replication for testing new features
- **Staging Environment**: Production-like environment for final testing
- **Production Environment**: Live system serving end users
- **Disaster Recovery**: Backup systems and data replication strategies
