# Code-Spherre Ecommerce Website

## Overview
**Code-Spherre Ecommerce Website** is a modern full-stack ecommerce platform built using:
- **Next.js** for frontend development
- **Sanity.io** as a headless CMS
- **Stripe** for secure payments
- **Tailwind CSS** for responsive UI design

This project allows users to browse products, add them to a cart, and securely checkout using Stripe. The backend is powered by **Sanity.io**, which manages product data and dynamic content.

---

## Features
✅ **Product Catalog** - Display products fetched from Sanity CMS
✅ **Shopping Cart** - Add, remove, and update items
✅ **Secure Payments** - Integrated with Stripe
✅ **Admin Dashboard** - Manage products and orders (Future Enhancement)
✅ **Mobile Responsive** - Optimized UI for all devices

---

## How to Install and Run Locally
### 1️⃣ Clone the Repository
```sh
git clone https://github.com/CodeSpherreDev/Code-Spherre_Ecommerce_Website.git
cd Code-Spherre_Ecommerce_Website
```

### 2️⃣ Install Dependencies
```sh
npm install
```

### 3️⃣ Setup Environment Variables
Create a `.env.local` file and add the following:
```env
NEXT_PUBLIC_SANITY_TOKEN =

NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY = 

NEXT_PUBLIC_STRIPE_SECRET_KEY = 
```

### 4️⃣ Run the Development Server
```sh
npm run dev
```
The app should now be available at [http://localhost:3000](http://localhost:3000)

---

## How to Contribute 🚀
1. **Fork the Repository**
2. **Create a New Branch** (`git checkout -b feature-name`)
3. **Make Your Changes**
4. **Commit and Push** (`git commit -m "Added new feature" && git push origin feature-name`)
5. **Create a Pull Request (PR)**

We welcome contributions! Feel free to fix bugs, add features, or improve the UI. 😊

---

## 🛠️ Known Issue: Server Error - Unable to Resolve Image URL
### ❌ Error Message
```
Error: Unable to resolve image URL from source (undefined)
```
### ✅ Solution
#### 1️⃣ Ensure Environment Variables Are Set Correctly
Check that `NEXT_PUBLIC_SANITY_PROJECT_ID` and `NEXT_PUBLIC_SANITY_DATASET` are correctly defined in `.env.local`.

#### 2️⃣ Fix the Image URL Function (`utils/image.js`)
Update the `urlFor` function to handle undefined values:
```js
import createImageUrlBuilder from '@sanity/image-url';
import { dataset, projectId } from '../env';

const builder = createImageUrlBuilder({ projectId, dataset });

export const urlFor = (source) => {
  if (!source) return '';
  return builder.image(source).url();
};
```

#### 3️⃣ Restart the Server
```sh
npm run dev
```

If the issue persists, check that your Sanity database contains valid image data.

---

## 📧 Contact & Support
For questions or contributions, feel free to reach out via GitHub Issues or email **codespherre.official@gmail.com**.
<br>
Our official website [code-spherre.netlify.app](code-spherre.netlify.app)

Happy Coding! 🚀

