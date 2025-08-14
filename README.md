## Workflows

### YooKassa

**Purpose:** full payment lifecycle with YooKassa: creating payments, validating input data (including e-mail via regex), retrying failed requests, handling payment statuses, processing refunds, logging, and recording results in Google Sheets.  
**Features:**

- E-mail validation using regular expressions.  
- Retries on network/temporary errors.  
- Centralized error handling with detailed messages.  
- Payment tracking in Google Sheets (append/update rows).  
- Separate branches for **success**, **pending**, **canceled**, **refunded**.  
- Ready-to-use HTTP Webhook nodes for YooKassa notifications.  
- Structured node names and a clear flowchart for easier maintenance.  

**Files:** `YooKassa.json`, `YooKassa.md`.  
**GitHub**

---

### GiggleGPTBot (RU)

**Purpose:** GPT (LLM) based bot/integration with message routing and business logic inside n8n.  
**Features:**

- Receiving messages (e.g., via Telegram/Slack/HTTP).  
- Contextual responses powered by LLM.  
- Ability to extend with functions/tools (scraping, parsing, API calls).  
- Flexible configuration of prompts and system messages.  

**Files:** `GiggleGPTBot.json`, `GiggleGPTBot.md`.  
**GitHub**
