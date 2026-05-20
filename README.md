# We will be building this in class

## Things You Need to Do

- Place this folder in your htdocs folder
- Start XAMPP, Apache and MySQL
- Using phpMyAdmin, create a new database and name it 'blog'. All lowercase.
- Import the SQL from the .sql folder in this repository
- Go to your browser and bring up the blog.php page

# CTEC 227 — Project 2: The Blog

Final project. You'll take the starter blog from class and turn it into a working multi-page blog application using **PHP, PDO, and MySQL**.

The starter code in this repo already does one thing: it reads every post from the `blog` database and dumps them onto a single page (`blog.php`). Your job is to grow it into something a real visitor could actually use — individual post pages, the ability to add and manage posts, and filtering by category and author.

Watch the Loom demo before you start: **https://www.loom.com/share/d952d4b02c2247258825333f172671bb** — the requirements below match what's shown there.

---

## What's in the starter code

```
.
├── blog.php              ← main page; lists all posts (already working)
├── css/                  ← stylesheets
├── inc/
│   ├── db_connect.inc.php  ← PDO connection to the `blog` database
│   └── navbar.inc.php      ← Bootstrap navbar include
├── sql/                  ← database dump — import this into phpMyAdmin
└── README.md             ← this file
```

The database has four tables: `post`, `author`, `category`, and `post_category` (a join table linking posts to categories — a post can have many categories).

---

## Local Setup

1. Clone your repo into your XAMPP **`htdocs`** folder.
   ```bash
   cd /path/to/xampp/htdocs
   git clone <your-repo-url>
   ```
2. Start **XAMPP**, then start **Apache** and **MySQL**.
3. Open **phpMyAdmin** (`http://localhost/phpmyadmin`).
4. Create a new database named **`blog`** (all lowercase).
5. Select the `blog` database, click **Import**, and upload the `.sql` file from the `sql/` folder.
6. Open `http://localhost/<your-repo-folder>/blog.php` in your browser. You should see the existing posts.

If you see a database connection error, open `inc/db_connect.inc.php` and confirm the host, username, and password match your local XAMPP setup (usually `localhost` / `root` / empty password).

---

## Project Requirements

> ⚠️ **Verify against the Loom demo.** The list below covers the standard expectations for this project. If anything in the video differs, the video wins.

### Required features

- **Post list page (`blog.php`)** — already done; make sure each post title links to its individual page.
- **Single post page (`post.php`)** — show one full post by `post_id` passed in the URL (e.g. `post.php?id=3`). Display the title, author, formatted date, all categories, and the full content.
- **Create a post (`add_post.php`)** — a form to add a new post. Must let the user pick the author and one or more categories. Insert into both `post` and `post_category`.
- **Edit a post (`edit_post.php?id=…`)** — pre-fill the form with the existing post data, then update on submit.
- **Delete a post** — with a confirmation prompt. Remove the post and its `post_category` rows.
- **Filter by category (`category.php?id=…`)** — show only the posts in one category.
- **Author page (`author.php?id=…`)** — show all posts written by one author.
- **Navbar links** — update `inc/navbar.inc.php` so users can reach all pages.

### Technical requirements

- Use **PDO with prepared statements** for *every* SQL query — no string concatenation, no `mysqli_*` calls.
- Use `require` / `include` for shared pieces (DB connection, navbar, header/footer).
- Escape any user-submitted content on output (`htmlspecialchars`) to prevent XSS.
- Style with Bootstrap 5 (already linked) — keep the look clean and consistent across pages.
- No PHP warnings or notices visible in the browser.

### Stretch goals (optional, for extra credit)

- Pagination on the main post list (e.g. 5 per page).
- Search by title or content keyword.
- A simple login so only logged-in users can add/edit/delete.
- A "drafts vs. published" flag on posts.

---

## How to Work on This Project

This repo is yours through **GitHub Classroom**. Develop in it directly — don't fork it elsewhere.

1. Make changes locally in `htdocs`.
2. Commit often, with clear messages:
   ```bash
   git add .
   git commit -m "Add single post page"
   git push
   ```
3. Push to `main` (or open a PR into `main` if you prefer that workflow). Your latest commit on `main` at the deadline is what gets graded.

**Don't commit:**
- `inc/db_connect.inc.php` changes that contain your personal DB password — keep the default XAMPP credentials.
- `.DS_Store`, editor folders (`.vscode/`, `.idea/`), or anything inside `xampp/`.

---

## Submission Checklist

Before the deadline, confirm:

- [ ] All required pages load without PHP errors
- [ ] You can add, edit, and delete posts and they persist in the database
- [ ] Category and author filter pages work
- [ ] Navbar links go to all your new pages
- [ ] All SQL uses PDO prepared statements
- [ ] Your final commit is pushed to `main` on GitHub
- [ ] The `sql/` file still imports cleanly into a fresh `blog` database (so your instructor can run your project)

---

## Getting Help

- Re-watch the Loom demo — most "how should this work?" questions are answered there.
- Check the PHP error log in XAMPP if a page goes blank.
- Bring specific questions (with the exact error message) to class or office hours.

Good luck!
