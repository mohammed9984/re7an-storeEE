# Vercel deploy fix

1. Merge these files into your project (keep your own `src/` folder, app code and schema).
   Files are correctly named with dots: eslint.config.mjs, postcss.config.mjs, next.config.ts.
   DELETE the old drizzle.config.json (drizzle.config.ts replaces it).
2. Create a free Postgres database (Neon, Supabase, or Vercel > Storage).
3. Copy .env.example to .env, set DATABASE_URL, then run:  npm install && npm run db:push
4. In Vercel > Settings > Environment Variables add DATABASE_URL (same value). Redeploy.
5. Any page/route that reads the database: add at the top
      export const dynamic = "force-dynamic";
6. Make sure your db client uses process.env.DATABASE_URL (see src/db/index.example.ts).
7. Never upload node_modules, .next or .env to GitHub/Vercel (.gitignore included).

Still failing? Paste the red lines from Vercel > Deployment > Build Logs.
