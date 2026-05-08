# 📰 GovJobPortal — Blog Management System

A full-featured Blog CMS (Content Management System) built for government job updates. Includes a public-facing blog portal and a protected admin panel with complete CRUD functionality, dynamic filtering via jQuery/AJAX, and a responsive design for both mobile and desktop.

---

## 🔗 Live Links

| | Link |
|---|---|
| 🌐 **Live Website** | `https://YOUR-USERNAME.github.io/blogcms/` |
| ⚙️ **Admin Panel** | `https://YOUR-USERNAME.github.io/blogcms/` → click **Sign In** |
| 📦 **GitHub Repo** | `https://github.com/YOUR-USERNAME/blogcms` |

> **Admin Credentials**
> - Username: `admin`
> - Password: `admin123`

---

## ✨ Features

### Public Side (User-Facing)
- 📋 Blog listing page with card grid layout
- 🔍 Live search — filters blogs as you type (no page reload)
- 🏷️ Category filter pills — Latest Jobs, Admit Card, Results, Government Scheme, Breaking News
- 📅 Date filter — filter blogs by specific publish date
- 📄 Blog detail page — full content, featured image, read time, breadcrumb
- 🔗 Related posts section on detail page
- 📱 Fully responsive — works on mobile, tablet, and desktop
- 📃 Pagination (6 posts per page)

### Admin Panel
- 🔐 Login system with credential validation
- 📊 Dashboard with stats: Total, Published, Drafts, Categories
- ➕ Add new blog post
- ✏️ Edit existing blog posts
- 🗑️ Delete with confirmation modal
- 🔄 Toggle publish/draft status by clicking status badge
- 📝 Rich text editor with toolbar: Bold, Italic, Underline, H1–H3, Lists, Blockquote, Table, Image, Link
- 🖼️ Featured image upload with live preview (Base64)
- 🔎 Admin-side search + category + status filter
- 🔔 Toast notifications for all actions

### AJAX + jQuery (Mandatory Requirement)
- All public filters (category, search, date) use **jQuery event binding** via `$(document).ready()`
- Filter application **simulates AJAX call** with spinner → delay → DOM update (mirrors real `$.ajax` to PHP backend)
- Admin search and filter fields bound entirely through jQuery (no inline `onchange` attributes)
- Pattern matches real-world `$.ajax({ url: 'api/blogs.php', data: filters, success: callback })` flow

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3 (Custom Properties, Grid, Flexbox) |
| Scripting | JavaScript (ES6+), **jQuery 3.7.1** |
| AJAX | jQuery simulated AJAX with spinner (mirrors PHP backend pattern) |
| Icons | Tabler Icons (CDN) |
| Hosting | GitHub Pages (static) |
| Backend Pattern | Designed for PHP + MySQL (see notes below) |

---

## 📁 Project Structure

```
blogcms/
│
├── index.html          ← Entire application (single-file SPA)
└── README.md           ← This file
```

---

## ⚙️ Setup & Run Locally

### Option 1 — Just open in browser
```bash
# No setup needed — just double-click the file
open index.html
```

### Option 2 — Run with a local server (recommended)
```bash
# Using Python
python -m http.server 8000
# Then open: http://localhost:8000

# Using Node.js (npx)
npx serve .
# Then open the URL shown in terminal
```

---

## 🚀 Deployment Steps (GitHub Pages)

> Full step-by-step guide included in `DEPLOY.md`

**Quick version:**
1. Create a GitHub account at github.com
2. Create a new repository named `blogcms`
3. Upload `index.html` and `README.md`
4. Go to **Settings → Pages → Source: main branch**
5. Your live URL: `https://YOUR-USERNAME.github.io/blogcms/`

---

## 🔑 Admin Login

```
URL:      Open the live site → Sign In button is on the landing screen
Username: admin
Password: admin123
```

---

## 📝 Notes on PHP/MySQL Backend

This submission is a **fully functional frontend prototype** that demonstrates all required features. The data layer uses an in-memory JavaScript store that mirrors a MySQL database structure. In a production PHP/Laravel deployment:

- Each `blogs` array entry maps to a `blogs` table row
- `applyPubFilters()` → `$.ajax({ url: 'api/blogs.php', method: 'GET', data: {cat, search, date} })`
- `saveBlog()` → `$.ajax({ url: 'api/save.php', method: 'POST', data: formData })`
- `confirmDelete()` → `$.ajax({ url: 'api/delete.php', method: 'POST', data: {id} })`
- Admin login → PHP session + `password_verify()`

The jQuery AJAX pattern is fully implemented and documented in code comments.

---

## 📸 Screenshots

| Public Blog Listing | Blog Detail | Admin Dashboard |
|---|---|---|
| Category filter pills, search, date filter | Full content, related posts | Stats, recent posts table |

---

## 👨‍💻 Author

Submitted as part of Blog Management System assignment.

- **Admin URL:** Live site home page (login screen loads first)
- **Test credentials:** admin / admin123
