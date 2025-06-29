# MediMeet – Doctor Appointment Platform

A full-stack web application for booking doctor appointments, video consultations, and managing healthcare online. Built with Next.js, Prisma, Clerk authentication, Tailwind CSS (dark mode), and Vonage Video API.

---

## Live Website

[https://medimeet-eight.vercel.app/](https://medimeet-eight.vercel.app/)

---

## Features

- **User Authentication:** Secure sign-up/sign-in with Clerk.
- **Patient Portal:** Book appointments, manage credits, and consult doctors via video.
- **Doctor Portal:** Manage availability, appointments, earnings, and payouts.
- **Admin Dashboard:** Approve doctors, manage payouts, and oversee platform activity.
- **Video Consultations:** Powered by Vonage Video API.
- **Credit System:** Patients purchase credits to book appointments; doctors earn credits and request payouts.
- **Responsive UI:** Modern, accessible, and fully dark-themed interface.
- **Integrated Chatbot:** HealthMate AI assistant powered by Omnidimension for appointment booking, rescheduling, and information.

---

## Tech Stack

- **Frontend:** Next.js, React, Tailwind CSS (dark mode)
- **Backend:** Next.js API routes, Prisma ORM, PostgreSQL
- **Authentication:** Clerk
- **Video Calls:** Vonage Video API
- **Styling:** Tailwind CSS, custom themes
- **ORM:** Prisma
- **AI Chatbot:** Omnidimension HealthMate

---

## Getting Started

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd medimeet-doc
```

### 2. Install dependencies

```bash
npm install
```

### 3. Set up environment variables

Create a `.env` file in the root directory and add the following (replace with your actual values):

```
DATABASE_URL=postgresql://<user>:<password>@<host>:<port>/<db>
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key
VONAGE_API_KEY=your_vonage_api_key
VONAGE_API_SECRET=your_vonage_api_secret
```

### 4. Set up the database

Run Prisma migrations to set up your PostgreSQL database:

```bash
npx prisma migrate deploy
npx prisma generate
```

### 5. Start the development server

```bash
npm run dev
```

Visit [http://localhost:3000](http://localhost:3000) or the [live site](https://medimeet-eight.vercel.app/) to view the app.

---

## Project Structure

- `app/` – Next.js app directory (pages, layouts, components)
- `components/` – Shared React components
- `lib/` – Utility functions and data
- `prisma/` – Prisma schema and migrations
- `public/` – Static assets

---

## Chatbot Integration (HealthMate by Omnidimension)

The MediMeet platform features a floating AI chatbot widget (HealthMate) in the bottom-right corner of every page. This assistant helps users book, reschedule, or cancel appointments, and provides information about doctors and the platform.

### How it works
- The chatbot UI is built in React and connects to your Omnidimension HealthMate agent.
- The agent is created and configured using the Omnidimension Python SDK.
- The frontend sends user messages to the agent's API/WebSocket endpoint and displays responses in real time.

### Setting up the Omnidimension Agent

1. **Create your agent using the Omnidimension Python SDK:**

```python
from omnidimension import Client

client = Client(api_key)
response = client.agent.create(
    name="HealthMate",
    welcome_message="""Hello, welcome to HealthMate! How can I assist you with your healthcare needs today? Are you looking to book, reschedule, or cancel an appointment, or do you need some information about a doctor?""",
    # ... (rest of your agent config)
)

print(f"Status: {response['status']}")
print(f"Created Agent: {response['json']}")

agent_id = response['json'].get('id')
```

2. **Deploy your agent and obtain the API or WebSocket endpoint** from Omnidimension.

3. **Configure the frontend chatbot widget** to use your agent's endpoint. Update the connection logic in `components/ChatbotWidget.jsx` to send/receive messages from your agent.

#### Example (HTTP):
```js
const OMNIDIM_API_URL = "https://api.omnidim.io/agent/YOUR_AGENT_ID/message";
// ...
const res = await fetch(OMNIDIM_API_URL, { method: "POST", headers: { "Content-Type": "application/json" }, body: JSON.stringify({ message: input }) });
const data = await res.json();
setMessages((msgs) => [...msgs, { from: 'bot', text: data.reply }]);
```

#### Example (WebSocket):
Refer to Omnidimension's documentation for WebSocket integration if available.

---

## Customization & Theming

- The app uses a **dark theme by default**. You can customize colors and themes in `globals.css` and Tailwind config.
- Update branding assets in the `public/` folder.

---

## License

MIT
