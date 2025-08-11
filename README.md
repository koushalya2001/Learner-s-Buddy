# Learner's Buddy: Brain Fog Detector Module

"Learner's Buddy" application is an EEG-based educational tool designed to assist children with motor disabilities. The Brain Fog Detector specifically addresses the challenge of identifying when a learner is confused and provides immediate assistance to resolve their doubts.

> "Doubts are the gateway to new discoveries."

## Core Functionality

The primary goal of this module is to create a more supportive and effective learning environment by automatically detecting a learner's confusion and offering resources to help them overcome it. The workflow is as follows:
1.  **Input:** The user provides their raw EEG signals (recorded while studying) and the topic they were learning.
2.  **Confusion Detection:** A machine learning model analyzes the EEG data to determine if the user is in a "confused" cognitive state.
3.  **Automated Assistance:** If confusion is detected, the application automatically scrapes the web for content related to the learning topic.
4.  **Resource Delivery:** The most relevant online resource is presented to the user, helping to clarify their doubts in real-time.

---

## How It Works

This module integrates signal processing, machine learning, and web automation to achieve its goal.

### 1. Machine Learning Model

*   **Algorithm:** The system uses an **XGBoost (Extreme Gradient Boosting)** classifier to predict the user's cognitive state. This algorithm was chosen for its high performance and scalability in handling complex datasets.
*   **Training Data:** The model was trained and validated on a public dataset from Kaggle, which contains EEG signals from college students watching Massive Open Online Course (MOOC) videos. The data is labeled to indicate whether the students felt confused by the content.
*   **Performance:** The classifier achieved a high accuracy of **91.6%**, ensuring reliable detection of a user's confusion. Model interpretability was analyzed using SHAP and LIME to understand feature impacts.

### 2. Web Scraping and Content Delivery

*   When the XGBoost model predicts a "confused" state, a web scraping process is triggered.
*   Using Python libraries such as `BeautifulSoup` and `Requests`, the application performs a search on the topic the user provided.
*   It then parses the search results, extracts the first and most relevant link (e.g., from Wikipedia), and automatically renders the content in the user's browser.

---

## How to Use

The user interface is designed for simplicity:
1.  Navigate to the **Brain Fog Detector** section of the Learner's Buddy application.
2.  Upload the file containing the raw EEG signals.
3.  Enter the topic being studied (e.g., "Trigonometry") in the provided text field.
4.  Click the **"CHECK STATUS NOW"** button.
5.  The system will analyze the data. If confusion is detected, a new browser tab will open with the scraped content, providing detailed information on the topic.

---

## Technology Stack

The module is built using a combination of powerful and modern technologies:

| Category              | Technology                             | Purpose                                             |
| :-------------------- | :------------------------------------- | :-------------------------------------------------- |
| **Language**          | Python                                 | Core programming language for the module.           |
| **Machine Learning**  | XGBoost, TensorFlow, Scikit-learn      | For building and training the detection model.      |
| **Web Framework**     | Flask                                  | To create the user interface and handle requests.   |
| **Web Automation**    | Selenium                               | To control the browser for displaying content.      |
| **Web Scraping**      | BeautifulSoup, Requests                | For extracting data from web pages.                 |
| **Model Explainability** | SHAP                                | To interpret and visualize the model's predictions. |
