# My Workflow – Setup Instructions

This workflow automatically fetches AI-related news, generates content, images, and posts to **Facebook, Twitter/X, LinkedIn**, and sends email notifications.

To run this workflow, you need to configure all API keys, access tokens, and OAuth credentials in **n8n**. Follow the steps below.

---

## 1. Environment Variables (Recommended)

For security, we recommend storing all API keys and access tokens in **environment variables** and referencing them in the workflow. Example `.env` file:

```env
# Facebook Graph API
FACEBOOK_GRAPH_API_TOKEN=your_facebook_access_token

# Twitter / X OAuth2
TWITTER_OAUTH2_TOKEN=your_twitter_oauth2_token

# LinkedIn Access Token
LINKEDIN_ACCESS_TOKEN=your_linkedin_access_token

# Google Gemini / OpenAI API
OPENAI_API_KEY=your_openai_api_key
GOOGLE_PALM_API_KEY=your_google_palm_api_key

# Hugging Face Inference API
HUGGINGFACE_API_KEY=your_huggingface_api_key

# NewsAPI
NEWS_API_KEY=your_newsapi_key

# Gmail OAuth2
GMAIL_CLIENT_ID=your_gmail_client_id
GMAIL_CLIENT_SECRET=your_gmail_client_secret
GMAIL_REFRESH_TOKEN=your_gmail_refresh_token
```

In n8n, you can reference them in nodes like:

```
={{ $env.FACEBOOK_GRAPH_API_TOKEN }}
```

---

## 2. Setting Up Facebook Graph API Node

1. Go to **Credentials → New → Facebook Graph API**.
2. Enter the **Access Token** from your Facebook Developer account.
3. Save and select the credential in the **Facebook Graph API node**.

---

## 3. Setting Up Twitter / X Node

1. Go to **Credentials → New → Twitter OAuth2 API**.
2. Enter **Client ID, Client Secret, and Access Token** from your Twitter Developer account.
3. Save and select the credential in the **Create Tweet node**.

---

## 4. Setting Up LinkedIn Nodes

1. Go to **Credentials → New → Header Auth (Generic)**.
2. Paste your **LinkedIn OAuth2 Bearer Token** in the Authorization header.
3. Use this credential in all **LinkedIn HTTP Request nodes**.

---

## 5. Setting Up Google Gemini / OpenAI Node

1. Go to **Credentials → New → OpenAI API** or Google PaLM API.
2. Paste the API key and save.
3. Select the credential in the **AI Agent / Chat nodes**.

---

## 6. Setting Up Hugging Face Node

1. Go to **Credentials → New → HTTP Header Auth**.
2. Paste your Hugging Face **API Key** in the `Authorization` header.
3. Select this credential in the **Hugging Face HTTP Request node**.

---

## 7. Setting Up NewsAPI Node

1. In the **Fetch Drone News node**, replace the `apiKey` in the URL with your NewsAPI key.
2. Optionally, store it in an **environment variable**.

Example:

```
https://newsapi.org/v2/everything?q=AI&language=en&sortBy=publishedAt&sources=bbc-news,reuters&pageSize=1&apiKey={{ $env.NEWS_API_KEY }}
```

---

## 8. Gmail / Email Node Setup

1. Go to **Credentials → New → Gmail OAuth2**.
2. Enter **Client ID, Client Secret, Refresh Token** from your Google Cloud project.
3. Use this credential in all Gmail nodes to send notifications.

---

## 9. Testing the Workflow

1. Activate your workflow in **n8n**.
2. Run the workflow manually to verify all nodes work.
3. Check your **social media accounts** and email for published posts and notifications.

