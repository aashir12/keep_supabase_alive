# 🟢 Supabase Keep-Alive Workflow

A lightweight GitHub Actions workflow that prevents your free-tier Supabase project from auto-pausing due to inactivity (Supabase pauses projects after **7 days** of no activity on the free plan).

## How It Works

Every **3 days**, this workflow sends a simple HTTP ping to your Supabase REST API. This counts as activity and resets the inactivity timer — keeping your project running 24/7.

---

## 🚀 Setup (5 minutes)

### 1. Fork or clone this repo to your GitHub account

```bash
git clone https://github.com/YOUR_USERNAME/supabase-keep-alive.git
cd supabase-keep-alive
```

### 2. Add GitHub Secrets

Go to your repo → **Settings** → **Secrets and variables** → **Actions** → **New repository secret**

Add these two secrets:

| Secret Name             | Value                                      |
|-------------------------|--------------------------------------------|
| `SUPABASE_URL`          | `https://jmwshthfzhztfmfkossk.supabase.co` |
| `SUPABASE_ANON_KEY`     | Your Supabase `anon` public key            |

> 🔑 Find your anon key in: **Supabase Dashboard** → **Project Settings** → **API**

### 3. Push to GitHub

```bash
git add .
git commit -m "Add Supabase keep-alive workflow"
git push origin main
```

### 4. Verify it works

- Go to your repo → **Actions** tab
- Click **"Supabase Keep-Alive"**
- Click **"Run workflow"** to test it manually
- You should see a green ✅ run

---

## ⚙️ Configuration

| Setting       | Default      | Description                        |
|---------------|--------------|------------------------------------|
| Schedule      | Every 3 days | Cron: `0 8 */3 * *`               |
| Trigger       | Auto + Manual | Can also be triggered manually    |

To change the frequency, edit the `cron` value in `.github/workflows/keep-alive.yml`.

---

## 📁 Project Details

- **Supabase Project:** `jmwshthfzhztfmfkossk`
- **Region:** `eu-central-1`
- **Status at setup:** `ACTIVE_HEALTHY`

---

## 🔒 Security Note

- The `anon` key is a **public-safe** key — it's designed to be used in client-side code
- It's still good practice to store it as a GitHub Secret rather than hardcoding it
- Never use your `service_role` key here

---

## 🛑 To Stop the Keep-Alive

Simply disable or delete the workflow file, or go to **Actions** → select the workflow → **Disable workflow**.
