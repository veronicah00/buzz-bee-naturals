# Deployment Guide for Buzz Bee Naturals

This document covers hosting the Flask backend and the static site.

## Step 1: Push code to GitHub
Your project is already pushed to:

https://github.com/veronicah00/buzz-bee-naturals.git

## Step 2: Deploy the app to Render
Render is a simple host for Python web apps, and this project is already set up to serve the frontend and backend from the same app.

1. Go to https://dashboard.render.com/
2. Create an account or sign in.
3. Click `New` → `Web Service`.
4. Connect your GitHub account and select `veronicah00/buzz-bee-naturals`.
5. Configure the service:
   - **Name**: `buzzbee-backend`
   - **Region**: Choose the nearest region
   - **Branch**: `main`
   - **Root Directory**: leave empty
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app --bind 0.0.0.0:$PORT`
6. Add environment variables:
   - `ADMIN_EMAIL` = `wanjiruveronicah2023@gmail.com`
   - `SMTP_SERVER` = `smtp.gmail.com`
   - `SMTP_PORT` = `587`
   - `SMTP_USERNAME` = `your-email@gmail.com`
   - `SMTP_PASSWORD` = `your-app-password`
   - `SMTP_USE_TLS` = `True`
   - `SMTP_FROM_EMAIL` = `your-email@gmail.com`
   - `DEBUG` = `False`
7. Click `Create Web Service`.

Render will build and deploy your app, then provide a public service URL.

### If Render fails to deploy
- Open the Render deploy log details.
- Copy the first error message or the failing step.
- Common issues:
  - missing packages in `requirements.txt`
  - invalid Python runtime
  - port or start command errors
- This repo now includes `runtime.txt` and `Procfile` to support Render.

## Step 3: Open the deployed site on your phone
After Render deploys, open the provided service URL on your phone, for example:

```
https://buzzbee-backend.onrender.com
```

The frontend is already configured to call `/api` from the same deployment, so you can test the order flow directly on your phone.

## Step 4: Test the live order flow
1. Open the deployed page on your phone.
2. Place an order.
3. Confirm the order reaches the Flask backend and returns success.
4. Confirm you receive the confirmation email at the customer and admin addresses.

## Notes
- GitHub Pages can host only the static front-end. The backend must be on a separate server (Render, Railway, etc.).
- The current backend works locally and returns `201` for valid orders.
- If email delivery fails, check the Render logs and verify your SMTP username/password and app password settings.
