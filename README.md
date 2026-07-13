# Lightning Chat App

Lightning Chat App is a React/Vite frontend with an Express, MongoDB, Cloudinary, and Socket.IO backend.

## Run locally

1. Copy `client/.env.example` to `client/.env` and set `VITE_BACKEND_URL`.
2. Copy `server/.env.example` to `server/.env` and provide the required credentials.
3. In separate terminals, run `npm install` followed by `npm run dev` in `client`, and `npm install` followed by `npm start` in `server`.

## Deploy the frontend to Netlify

The included `netlify.toml` configures Netlify to build the `client` directory with `npm run build` and publish `client/dist`. It also redirects all routes to `index.html`, so direct visits to `/login` and `/profile` work.

1. Push this repository to GitHub without either `.env` file.
2. Deploy the `server` to a Node-compatible host that supports persistent WebSocket connections (for example Render or Railway). Netlify static hosting cannot run this Express/Socket.IO server.
3. Set `FRONTEND_URL` on that backend to your deployed Netlify site URL, for example `https://your-site.netlify.app`.
4. In Netlify, set `VITE_BACKEND_URL` to the public HTTPS URL of the deployed backend, with no trailing slash.
5. Deploy. Netlify uses the committed `netlify.toml`; its detected settings should be base directory `client`, build command `npm run build`, and publish directory `dist`.

`VITE_*` variables are embedded in browser code at build time. Never put database, JWT, Cloudinary secret, or any other private value in a Netlify environment variable beginning with `VITE_`.
