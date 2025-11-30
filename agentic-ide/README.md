# Agentic IDE

A modified version of code-server with integrated AI models and agentic features for unlimited workspace creation.

## Features

- Web-based VSCode IDE
- Multiple AI models (GPT-4, GPT-3.5)
- Agentic AI for code tasks
- Unlimited workspace creation

## Setup

1. Install Ollama for local AI models:
   ```
   # Download from https://ollama.ai and install
   # Pull models: ollama pull llama2, ollama pull codellama
   ```

2. Clone and build:
   ```
   cd agentic-ide/code-server
   git submodule update --init  # Initialize vscode submodule
   npm install
   npm run build
   ```

3. Set environment variables (optional for OpenAI):
   ```
   export OPENAI_API_KEY=your_api_key  # Optional, local models don't need it
   ```

4. Run Ollama server in background:
   ```
   ollama serve
   ```

5. Run the IDE:
   ```
   node out/node/entry.js --port 8080
   ```

4. Access at http://localhost:8080

## API Endpoints

- POST /ai/chat: Chat with AI models
- POST /ai/agent: Run agentic tasks
- GET /ai/models: List available models
- POST /ai/create-workspace: Create new workspace

## Deployment

### Self-Hosted
Deploy on a Linux server with Node.js 22, set OPENAI_API_KEY, and run as above.

### Free Platforms
Deploy on free hosting platforms:

#### Vercel
1. Sign up at vercel.com
2. Create new project
3. Connect your GitHub repo containing this code
4. Set build settings:
   - Build Command: npm run build
   - Output Directory: out
   - Install Command: npm install
5. Set environment variables: OPENAI_API_KEY (optional)
6. Deploy
Note: Vercel is serverless, so for full IDE features, Railway or Render may be better.

#### Railway
1. Sign up at railway.app
2. Create new project from GitHub
3. Push this code to a GitHub repo
4. Connect repo to Railway
5. Set environment variables: OPENAI_API_KEY
6. Deploy

#### Render
1. Sign up at render.com
2. Create Web Service
3. Connect GitHub repo
4. Set build command: npm install && npm run build
5. Start command: node out/node/entry.js --port $PORT --auth none
6. Set OPENAI_API_KEY in environment

#### Heroku
1. Sign up at heroku.com
2. Create app
3. Push code to Heroku Git
4. Set OPENAI_API_KEY config var
5. Heroku will auto-detect Node.js

Note: Free tiers have limitations; upgrade for persistent storage and more resources.