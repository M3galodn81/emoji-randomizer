# 🎲 Emoji Randomizer (Vue 3 + TypeScript + Vite)

A fun little **web dev project** that fetches and displays a random emoji using the [EmojiHub API](https://github.com/cheatsnake/emojihub).  
Built with **Vue 3**, **TypeScript**, **Vite**, **TailwindCSS**, and **shadcn/ui** components.  

---

## 🚀 Features
- 🎉 Fetches a random emoji from [EmojiHub](https://emojihub.yurace.pro/api/random)
- 📝 Displays:
  - Emoji Name
  - Emoji Group
  - Actual Emoji (rendered with HTML code)
  - Unicode
- 🔄 Randomize button to get a new emoji
- 🎨 Clean UI with TailwindCSS + shadcn/ui components

---

## 🛠️ Tech Stack
- [Vue 3](https://vuejs.org/) with `<script setup>`
- [TypeScript](https://www.typescriptlang.org/)
- [Vite](https://vitejs.dev/)
- [TailwindCSS](https://tailwindcss.com/) for styling
- [shadcn/ui](https://ui.shadcn.com/) for prebuilt UI components
- [Axios](https://axios-http.com/) for API requests
- [EmojiHub API](https://github.com/cheatsnake/emojihub) for random emoji data

---

## 📦 Installation

Clone the repo and install dependencies:

```bash
git clone https://github.com/M3galodn81/emoji-randomizer.git
cd emoji-randomizer
npm install
````

Run the dev server:

```bash
npm run dev
```

Build for production:

```bash
npm run build
```

Preview build:

```bash
npm run preview
```

---

## 📸 Demo

When you load the app, it fetches a random emoji and shows:

```
Name: Hugging Face
Group: Smileys and People
😀
HTML Code: &#129303;
Unicode: U+1F917
```

Click the **Randomize** button to fetch another one!

---

## ⚡ Project Structure

```
src/
 ├─ components/
 │   ├─ ui/         # shadcn/ui components
 ├─ App.vue
 ├─ main.ts
 └─ ...
```

---

## 🌍 API Reference

* **Endpoint**: `https://emojihub.yurace.pro/api/random`
* **Response Example**:

```json
{
  "name": "hugging face",
  "category": "smileys and people",
  "group": "face positive",
  "htmlCode": ["&#129303;"],
  "unicode": ["U+1F917"]
}
```

---

## 📌 To Do / Possible Improvements

* Add copy-to-clipboard for emoji
* Show multiple random emojis at once
* History with clipboard 
---

