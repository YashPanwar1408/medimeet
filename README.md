# MediMeet – Doctor Appointment Platform

A full-stack web application for booking doctor appointments, video consultations, and managing healthcare online. Built with Next.js, Prisma, Clerk authentication, Tailwind CSS (dark mode), and Vonage Video API.

---

## Features

- **User Authentication:** Secure sign-up/sign-in with Clerk.
- **Patient Portal:** Book appointments, manage credits, and consult doctors via video.
- **Doctor Portal:** Manage availability, appointments, earnings, and payouts.
- **Admin Dashboard:** Approve doctors, manage payouts, and oversee platform activity.
- **Video Consultations:** Powered by Vonage Video API.
- **Credit System:** Patients purchase credits to book appointments; doctors earn credits and request payouts.
- **Responsive UI:** Modern, accessible, and fully dark-themed interface.

---

## Tech Stack

- **Frontend:** Next.js, React, Tailwind CSS (dark mode)
- **Backend:** Next.js API routes, Prisma ORM, PostgreSQL
- **Authentication:** Clerk
- **Video Calls:** Vonage Video API
- **Styling:** Tailwind CSS, custom themes
- **ORM:** Prisma

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

Visit [http://localhost:3000](http://localhost:3000) to view the app.

---

## Project Structure

- `app/` – Next.js app directory (pages, layouts, components)
- `components/` – Shared React components
- `lib/` – Utility functions and data
- `prisma/` – Prisma schema and migrations
- `public/` – Static assets

---

## Customization & Theming

- The app uses a **dark theme by default**. You can customize colors and themes in `globals.css` and Tailwind config.
- Update branding assets in the `public/` folder.

---

## License

MIT
