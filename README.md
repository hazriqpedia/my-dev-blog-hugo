# hazriqpedia.github.io – My Hugo Dev Blog ✍️

This site is powered by [Hugo](https://gohugo.io/) and deployed via GitHub Pages at:  
🌐 **https://hazriqpedia.github.io**

## 🛠️ Requirements

- [Install Hugo](https://gohugo.io/getting-started/installing/)
- Git
- A GitHub repo (like this one)

## 🚀 Quick Commands

### ▶️ Run the site locally

Start a local server (live reload enabled):

```bash
hugo server
```

Then open: [http://localhost:1313](http://localhost:1313)

## ✍️ Writing Content

### ➕ Add a New Post

```bash
hugo new posts/my-new-post.md
```

Then:

- Edit the front matter (`title`, `date`, `draft: true`)
- Write your content in Markdown
- Set `draft: false` when you're ready to publish

### ➕ Add a New Page

Example:

```bash
hugo new about.md
```

or:

```bash
hugo new about/_index.md
```

Then edit the file under `content/about.md`.

## ❌ Remove a Post/Page

Delete the file directly:

```bash
rm content/posts/my-old-post.md
```

## 📦 Static Assets

- Put files in `static/`
- Example: `static/images/me.png` → use as `/images/me.png` in Markdown

## ⚙️ Configuration

Edit `config.toml` to customize:

- Site title/description
- Menus
- Theme settings (using PaperMod)

## 🚀 Publishing to GitHub Pages

1. Build the site:

```bash
hugo
```

2. Navigate to `public/`:

```bash
cd public
```

3. Commit and push:

```bash
git add .
git commit -m "Deploy"
git push origin gh-pages --force
```

## (Optional) Setup `gh-pages` with Git Worktree

```bash
git worktree add -B gh-pages public origin/gh-pages
```

This makes `public/` track the `gh-pages` branch directly.

## 🙌 Credits

- Generator: [Hugo](https://gohugo.io)
- Theme: [PaperMod](https://github.com/adityatelange/hugo-PaperMod)
