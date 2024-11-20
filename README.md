<div align="center">
  <br />
    <a href="https://youtu.be/lEflo_sc82g?feature=shared" target="_blank">
      <img src="https://firebasestorage.googleapis.com/v0/b/project-gallery-tool.appspot.com/o/gallerytool%2FUntitled%20design.png?alt=media&token=ea844584-f16e-4590-b156-b5fb7ef139c7" alt="Project Banner">
    </a>
  <br />

  <div>
   <img
  src="https://img.shields.io/badge/Next.js-0070F3?style=for-the-badge&logo=next.js&logoColor=white"
  alt="Next.js"
/>
     <img
        src="https://img.shields.io/badge/-NextAuth-0000FF?style=for-the-badge&logoColor=white&logo=next.js"
        alt="NextAuth"
      />
    <img src="https://img.shields.io/badge/-React_Hook_Form-black?style=for-the-badge&logoColor=white&logo=react&color=EC5990" alt="reacthookform" />
    <img src="https://img.shields.io/badge/-Tailwind_CSS-black?style=for-the-badge&logoColor=white&logo=tailwindcss&color=06B6D4" alt="tailwindcss" />
    <img src="https://img.shields.io/badge/-Firebase-orange?style=for-the-badge&logo=firebase&logoColor=black&color=FFCA28" alt="firebase" />
  </div>

  <h3 align="center">A HealthCare Management System</h3>
</div>

## 📋 <a name="table">Table of Contents</a>

1. 🤖 [Introduction](#introduction)
2. ⚙️ [Tech Stack](#tech-stack)
3. 🔋 [Features](#features)
4. 🤸 [Quick Start](#quick-start)
5. 🕸️ [Snippets (Code to Copy)](#snippets)
6. 🔗 [Assets](#links)
7. 🚀 [More](#more)

## <a name="introduction">🤖 Introduction</a>

Showcase your projects with a full-stack app built using Next.js. This tool integrates React, Firebase, and NextAuth for seamless authentication, while Tailwind CSS offers sleek styling. Enhance form management with React Hook Form or Yup, and leverage Google Cloud for robust hosting and scalability. Perfect for developers!

If you're getting started and need assistance or face any bugs, join our active Discord community with over **34k+** members. It's a place where people help each other out.

<a href="https://discord.com/invite/n6EdbFJ" target="_blank"><img src="https://github.com/sujatagunale/EasyRead/assets/151519281/618f4872-1e10-42da-8213-1d69e486d02e" /></a>

## <a name="tech-stack">⚙️ Tech Stack</a>

- Next.js
- Firebase
- NextAuth
- TailwindCSS
- Flowbite
- ReactHookForm

## <a name="features">🔋 Features</a>

👉 **Register as a User**: Users can sign up and create a personal projects.

👉 **Add a New Project**: Allows authenticated users to upload their projects (e.g., images, videos, descriptions) to the gallery.

👉 **Manage Projects on Admin Side**: Administrators can efficiently view and handle all created projects.

👉 **Project Deleting**: Administrators have the ability to delete any project as needed.

👉 **Complete Responsiveness**: The application works seamlessly on all device types and screen sizes.

👉 **File Upload Using Firebase firestore**: Users can upload and store files securely within the app using firebase firestore  services.

and many more, including code architecture and reusability

## <a name="quick-start">🤸 Quick Start</a>

Follow these steps to set up the project locally on your machine.

**Prerequisites**

Make sure you have the following installed on your machine:

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/en)
- [yarn](https://yarnpkg.com/) (Package Manager)

**Cloning the Repository**

```bash
git clone https://github.com/Hi-Dear-486/Projects-Gallery-Tool.git
cd ./
```

**Installation**

Install the project dependencies using yarn:

```bash
yarn install
```

**Set Up Environment Variables**

Create a new file named `.env.local` in the root of your project and add the following content:

```env
#Firebase
NEXT_PUBLIC_FIREBASE_API_KEY
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN
NEXT_PUBLIC_FIREBASE_PROJECT_ID
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID
NEXT_PUBLIC_FIREBASE_APP_ID
```

Replace the placeholder values with your actual Firebase credentials. You can obtain these credentials by signing up on the [Firebase website (https://firebase.google.com/).

**Running the Project**

```bash
yarn  run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to view the project.

## <a name="snippets">🕸️ Snippets</a>

<details>
<summary><code>tailwind.config.js</code></summary>

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx,mdx}",
    "./components/**/*.{js,ts,jsx,tsx,mdx}",
    "./app/**/*.{js,ts,jsx,tsx,mdx}",
  ],
  theme: {
    extend: {
      colors: {
        background: "var(--background)",
        foreground: "var(--foreground)",
      },
      boxShadow: {
        5: "rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px",
      },
    },
  },
  plugins: [],
};
```

</details>

<details>
<summary><code>app/globals.css</code></summary>

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

:root {
  --background: #ffffff;
  --foreground: #171717;
}

@media (prefers-color-scheme: dark) {
  :root {
    --background: #0a0a0a;
    --foreground: #ededed;
  }
}

body {
  color: var(--foreground);
  background: var(--background);
  font-family: Arial, Helvetica, sans-serif;
}
```

</details>

<details>
<summary><code>app/(authprovider)/AuthProvider.jsx</code></summary>

```javascript
"use client";
import React from "react";
import { SessionProvider } from "next-auth/react";
const Authprovider = ({ children }) => {
  return <SessionProvider>{children}</SessionProvider>;
};

export default Authprovider;
```
</details>

<details>
<summary><code>app/api/auth/[...nextauth]/route.js</code></summary>

```javascript
import NextAuth from "next-auth";
import GoogleProvider from "next-auth/providers/google";

const handler = NextAuth({
  providers: [
    GoogleProvider({
      clientId: process.env.GOOGLE_Client_ID,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET,
    }),
  ],
});

export { handler as GET, handler as POST };
</details>

<details>
<summary><code>lib/firebase.js</code></summary>

```javscript
import { initializeApp } from "firebase/app";

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: process.env.NEXT_PUBLIC_FIREBASE_API_KEY,
  authDomain: process.env.NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN,
  projectId: process.env.NEXT_PUBLIC_FIREBASE_PROJECT_ID,
  storageBucket: process.env.NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET,
  messagingSenderId: process.env.NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID,
  appId: process.env.NEXT_PUBLIC_FIREBASE_APP_ID,
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
export default app;
```
</details>

## <a name="more">🚀 More</a>
**Advance your skills with Next.js 14**

Enjoyed creating this project? Dive deeper  for a richer learning adventure. They're packed with detailed explanations, cool features, and exercises to boost your skills. Give it a go!

<a href="https://github.com/Hi-Dear-486/Movie-flix-App" target="_blank">
<img src="https://github.com/Hi-Dear-486/Movie-flix-App/blob/master/movie.JPG" alt="Project Banner">
</a>

<br />
<br />

#
