# Creatorly (NexusAI Creator Marketplace) - Environment Configuration

This project is built to run out-of-the-box using resilient fallback engines for database storage, AI generations, and escrow payments if external API keys are omitted.

## Environment Variables (.env)

Place a `.env` file in the `backend/` directory with the following variables:

| Variable | Required? | Default / Example | Purpose |
| :--- | :--- | :--- | :--- |
| `PORT` | Optional | `5000` | Port for the Express backend server |
| `NODE_ENV` | Optional | `development` | Environment mode (`development` or `production`) |
| `JWT_SECRET` | Required | `supersecret_nexus_ai_jwt_key_2026` | Secret key used to sign and verify session JWTs |
| `MONGO_URI` | Optional | `mongodb://localhost:27017/nexus_ai_creator_marketplace` | MongoDB connection string. If omitted or disconnected, automatically falls back to `backend/data/nexus_database.json` |
| `GEMINI_API_KEY` | Optional | *(empty)* | Google Gemini API key for live multi-modal AI studio generations. If empty, uses built-in smart generative engine |
| `OPENAI_API_KEY` | Optional | *(empty)* | Optional secondary LLM key |
| `STRIPE_SECRET_KEY` | Optional | *(empty)* | Stripe secret key for live payment checkouts. If empty, uses the built-in 256-Bit Escrow Vault Simulator |
| `STRIPE_PUBLISHABLE_KEY` | Optional | *(empty)* | Stripe public publishable key for client-side forms |

## Installation & Running

### 1. Install Dependencies
```bash
# In backend/
cd backend
npm install

# In frontend/
cd ../frontend
npm install
```

### 2. Build Frontend
```bash
cd frontend
npm run build
```

### 3. Start Backend & Static Serving
```bash
cd backend
node server.js
```
The application will be accessible at `http://localhost:5000`.
