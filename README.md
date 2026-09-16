# Free AI Paraphraser

A small Vercel-ready paraphrasing website backed by DeepSeek. The API key stays in a server-side environment variable and is never sent to visitors.

## Deploy to Vercel

1. Create an empty GitHub repository and upload this project's files.
2. In Vercel, choose **Add New → Project** and import that repository.
3. Open **Environment Variables** and add:
   - `DEEPSEEK_API_KEY`: your DeepSeek API key
   - `DEEPSEEK_MODEL`: `deepseek-v4-flash` (optional; this is the default)
4. Select **Deploy**. No build command or output directory is needed.

For local testing with Vercel CLI:

```powershell
Copy-Item .env.example .env.local
# Edit .env.local and add your key, then:
npx vercel dev
```

Do not commit `.env` or `.env.local`.

## Rate-limit note

The browser tracks three successful rewrites per UTC day. The API also applies a lightweight per-IP in-memory limit. Because Vercel Functions can restart or run as multiple instances, strict production rate limiting requires a shared store such as Vercel KV or Upstash Redis.
