# n8n WhatsApp Sales Agent 🛒🤖

![n8n Workflow Architecture](n8n-whatsapp-bot(Twilio).jpg)

An intelligent, fully automated WhatsApp storefront and customer support agent built entirely with **n8n**. 

This project goes beyond a simple rule-based chatbot. It acts as a digital sales representative that can understand complex customer intents, remember conversation history, recommend products using AI, and manage orders—all synced in real-time with a Google Sheets database.

*(Note: The workflow JSON is currently kept private, but the architecture and capabilities are documented below.)*

## ✨ What It Can Do

* 🧠 **Smart Intent Routing:** Uses custom logic to instantly distinguish between exact product lookups, requests for AI recommendations, order placements, and tracking inquiries.
* 🗣️ **Multilingual Support:** Naturally understands and processes English, Bangla (বাংলা), and Banglish. It replies in the same language style the customer uses.
* 💾 **Contextual Memory (Redis):** Remembers what the customer was just talking about. If a user asks about an "iPhone 15 Pro" and follows up with "Does it come in blue?", the agent knows exactly which product they mean without asking them to repeat themselves.
* 📊 **Live Database Sync:** Connected directly to Google Sheets. It reads live inventory, prices, and specs, and automatically updates order statuses.
* 🤖 **AI Sales Assistant:** Powered by an LLM to handle ambiguous requests. If a customer asks, *"Which laptop is best for a university student under 100k?"*, the AI reads the live product catalog and provides a tailored recommendation.
* 🚚 **Automated Order Tracking:** Customers can type "track my order" to instantly get their real-time delivery status. The system also pushes automatic WhatsApp updates when an order shifts from *Pending* to *Shipped* or *Delivered*.

## 🛠️ Tech Stack

* **Workflow Automation:** [n8n](https://n8n.io/)
* **Messaging API:** Twilio (WhatsApp Business API)
* **State Management / Memory:** Redis (via Upstash)
* **Database & CRM:** Google Sheets API
* **AI / LLM:** OpenAI / OpenRouter

## 🔄 How The System Flows

1.  **Message Received:** A customer sends a WhatsApp message which is caught by an n8n Webhook.
2.  **Memory Retrieval:** The system fetches the customer's conversation history and last viewed product from Redis.
3.  **Intent Detection:** The core engine analyzes the text to determine the user's goal (Greeting, Exact Lookup, AI Query, Order, or Tracking).
4.  **Dynamic Routing:** * *Exact Lookups* bypass the AI for lightning-fast database replies.
    * *Recommendation Queries* are routed to the AI Agent equipped with a live product-catalog tool.
    * *Order/Tracking intents* trigger specific CRM workflows.
5.  **State Update & Reply:** The new context is saved back to Redis, and a formatted WhatsApp reply is sent to the customer.

---

## 👨‍💻 About the Developer

**Sheikh Mainul Islam** *AI & Automation Consultant* I specialize in building intelligent automation systems that streamline business workflows. Currently pursuing my BSc in Computer Science and Engineering (CSE) at the University of Asia Pacific (UAP), I am passionate about bridging the gap between complex AI logic and practical, revenue-generating business applications.

🔗 **GitHub:** [@Sheikh-Mainul-Islam](https://github.com/Sheikh-Mainul-Islam)
