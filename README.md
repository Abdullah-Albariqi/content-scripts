# Content Scripts

**A content dispatcher: drop in photos or a video and it writes the caption with AI and publishes to TikTok, Instagram and Threads.**

## The problem

Posting the same content to several platforms for several brands means rewriting captions in each brand's voice and going through each platform's upload flow by hand, every single day.

## The solution

- **Media routing.** Detects whether an upload is a video or a set of images, and sends it to the right platform flow.
- **Brand-aware captions.** The Claude API writes captions in each brand's own tone and personality.
- **TikTok.** Uses the full Content Posting API flow: initialise the upload, upload the video in chunks, then publish.
- **Instagram and Threads.** Uses the Meta Graph API for carousels, Reels and Threads posts.
- **Multi-brand.** Each brand has its own profile, and all credentials are read from environment variables.
- **Dispatcher.** A small Flask app with a job-status endpoint.

## How it works

```
Upload media + short description
        │
        ▼
content_engine  ──detects media type──▶  ai_captioner (Claude API, brand voice)
        │
        ├──▶ tiktok_manager            (init → chunked upload → publish)
        └──▶ instagram_threads_manager (carousel · reel · threads post)
        │
        ▼
Job status via the Flask dispatcher
```

## Tech stack

Python · Flask · Claude API · TikTok Content Posting API · Meta Graph API (Instagram, Threads)

## Screenshots

No screenshots yet: the dispatcher's web front-end isn't included in this version.

## Status

🧪 **Prototype**

---

Source code is private and available on request. More about me: [Abdullah-Albariqi](https://github.com/Abdullah-Albariqi)
