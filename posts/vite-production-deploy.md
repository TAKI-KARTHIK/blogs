---
title: "From Localhost to Production with Vite and Cloudflare Pages"
date: "2026-02-27"
---
# From Localhost to Production: Deploying a Vite App on Cloudflare Pages Without Losing Your Mind

> “It works on my machine.”
>
> — Every developer before production breaks everything.

If you’ve ever built a frontend app using Vite and thought deployment would be “just a click away,” this blog is for you.

This is the story of how I deployed my Vite + React app to Cloudflare Pages — and the unexpected issues I ran into along the way.

This isn’t just a tutorial.  
This is what actually happens between localhost and production.

---

## The Stack

Here’s what I used:

- Vite + React
- Cloudflare Pages
- Custom domain (karthikr.dev)
- Environment variables
- GitHub for deployment

Simple stack. Nothing fancy.

And yet… production still found ways to humble me.

---

## Step 1: Preparing for Deployment

When using Vite, your production build command is:

```bash
npm run build
```

This generates a `dist/` folder.

On Cloudflare Pages, the important settings are:

- **Build command:** `npm run build`
- **Build output directory:** `dist`

If this is wrong, your app won’t deploy properly.

---

## Step 2: Deploying to Cloudflare Pages

I connected my GitHub repository to Cloudflare Pages.

Cloudflare automatically:
- Installs dependencies
- Runs the build command
- Deploys the output

Sounds smooth, right?

Well… not exactly.

---

## Problem #1: The Favicon Was Loading… But Nothing Else

This one was confusing.

The page was blank.  
But the favicon showed up.

What was happening?

The issue was either an incorrect build output directory, or if your app uses React Router, a missing _redirects file. Without it, Cloudflare can't serve index.html for deep links and returns a 404 instead.

**Lesson:**  
Always double-check your build output directory.

---

## Problem #2: Environment Variables Were Not Working

On localhost, everything worked.

In production?  
Undefined variables.

Why?

Because Vite requires environment variables to start with:

```env
VITE_
```

Example:

```env
VITE_API_URL=https://api.example.com
```

If you don’t prefix variables with `VITE_`, they won’t be exposed to your frontend code.

Also:

After adding environment variables in Cloudflare Pages:
- You must redeploy.
- They are not automatically injected into previous builds.

**Lesson:**  
Production environment variables are not the same as your local `.env` file.

---

## Problem #3: Custom Domain Setup

I wanted my project live on:

```
karthikr.dev
```

Steps:

1. Add the custom domain inside Cloudflare Pages.
2. Ensure DNS is correctly configured.
3. Wait for SSL provisioning.

Make sure you have at least one successful deployment before expecting the domain to resolve correctly.

**Lesson:**  
Deploy first. Connect the domain second.

---

## What I Learned

Deployment is not just:

Build → Upload → Done

It’s about understanding:

- How build tools generate assets
- How static hosting works
- How DNS connects your domain
- How environment variables are injected
- How caching behaves in production

Localhost hides complexity.

Production exposes it.

---

## What I’d Do Differently Next Time

- Validate `.env` naming early
- Keep deployment notes
- Test the production build locally:

```bash
npm run build
npm run preview
```

- Treat production like a separate system

---

## Final Thoughts

Your first production deployment will break.

That’s normal.

What matters is:
- Debugging calmly
- Reading logs carefully
- Understanding systems instead of guessing

If you're building and deploying your own projects, you're already ahead.

Keep shipping. Keep breaking. Keep learning.

— Karthik R