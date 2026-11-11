# Project Architecture & Asset Naming Conventions

This repository follows a strict structure and naming convention to ensure cross-platform compatibility, maintainable code, and seamless Tailwind CSS integration.

---

## 📁 Directory Structure & File Placement

To keep the project organized, all new HTML views and images must be placed in their correct directories. **Do not place loose images directly inside the `src/` folder.**

```text
├── src/
│   ├── assets/              
│   │   └── images/          <-- ALL images, icons, and illustrations go here
│   │
│   ├── pages/               <-- ALL new HTML pages/screens go here
│   │   ├── auth/            (e.g., login.html, register.html)
│   │   ├── dashboard/       (e.g., overview.html)
│   │   └── settings.html    (Individual page)
│   │
│   ├── css/                 
│   │   └── input.css        (Tailwind source file)
│   │
│   └── index.html           (Main entry point of the application)
├── dist/                    (Compiled production-ready assets and HTML)
├── tailwind.config.js       (Tailwind configuration)
└── README.md
```

### 📍 Guidelines for adding new files:

1. **Images and Multimedia:** All files must be uploaded inside **`src/assets/images/`**. 
2. **New HTML Pages (Views):** All new screens must be created inside **`src/pages/`**. You can create individual files (e.g., `src/pages/about.html`) or group them in subfolders by feature (e.g., `src/pages/auth/login.html`).

> ⚠️ **Important Tailwind Note:** For Tailwind to detect and compile utility classes in your new HTML files, verify that your `tailwind.config.js` includes the `pages` directory in the `content` array:
> ```javascript
> content: ["./src/index.html", "./src/pages/**/*.html"],
> ```

---

## 🚀 The Golden Rule for Assets

Always use **`snake_case`** (lowercase letters, numbers, and underscores) for all filenames. 

* **Never** use uppercase letters (e.g., `ImageLogo.png`).
* **Never** use spaces (e.g., `ic menu open.svg`).
* **Never** use special characters or accents (e.g., `ñ`, `á`, `ç`).

---

## 🧱 Asset Naming Syntax

All asset filenames must follow a simple two-segment structure:

```text
[type]_[description].[extension]
```

### Breakdown & Schema

| Segment | Description | Common Prefixes / Examples |
| :--- | :--- | :--- |
| `[type]` | The category or nature of the asset. | `img` (image/photo), `ic` (icon), `bg` (background), `ill` (illustration) |
| `[description]` | What the element represents (clear and brief). | `logo`, `arrow_left`, `banner`, `avatar_default`, `cart_empty` |

---

## 🛠️ Examples in Action

* **Main App Logo:** `img_logo.png`
* **Back Button Arrow Icon:** `ic_arrow_left.svg`
* **Authentication Screen Wallpaper:** `bg_wallpaper.jpg`
* **Empty Cart Visual State:** `ill_cart_empty.svg`
* **Default User Avatar:** `img_avatar_default.webp`

---

## ⚠️ Best Practices & Image Formats

1. **Semantic over Descriptive:** Name assets based on **what they represent or do**, not what they look like. Use `ic_menu.svg` instead of `ic_three_lines.svg`.
2. **Language Consistency:** All assets and file paths must be named in **English** to match standard development practices.
3. **Format Standardization (Keep it lightweight):** 
   * **`.svg`**: Mandatory for vector icons, shapes, and logos. They never pixelate and weigh almost nothing.
   * **`.webp` / `.avif`**: Highly recommended for photographs and standard UI images. They offer up to 30% better compression than JPEG/PNG without losing quality.
   * **`.png`**: Use only when transparency (alpha channel) is required and `.webp` is not an option.
   * **`.jpg` / `.jpeg`**: Use for heavy photographs only if modern formats are unavailable, ensuring they are compressed before uploading.
