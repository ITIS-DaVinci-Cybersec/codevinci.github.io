# CodeVinci - CTF Writeups

🏴 A CTF team blog built with [Hugo](https://gohugo.io/) and [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## 🚀 Quick Start

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.124.0+)
- Git

### Local Development

```bash
# Clone the repository
git clone https://github.com/codevinci/codevinci.github.io.git
cd codevinci.github.io

# Run local server
hugo server -D

# Open http://localhost:1313
```

## 📝 Creating New Writeups

Use the writeup archetype for consistent formatting:

```bash
hugo new --kind writeup posts/ctf-name-challenge-name.md
```

This creates a new writeup with all the necessary frontmatter.

## 📁 Project Structure

```
.
├── archetypes/
│   ├── default.md      # Default content template
│   └── writeup.md      # CTF writeup template
├── assets/
│   └── css/extended/   # Custom CSS overrides
├── content/
│   ├── about.md        # About page
│   ├── archives.md     # Archives page
│   ├── search.md       # Search page
│   ├── team.md         # Team page
│   └── posts/          # Writeups go here
├── static/
│   ├── favicon.svg     # Site favicon
│   └── images/         # Images
├── themes/
│   └── PaperMod/       # Theme
└── hugo.toml           # Site configuration
```

## ✏️ Writeup Format

Each writeup should include:

1. **Challenge Info** - CTF name, category, difficulty, points
2. **Description** - Original challenge description
3. **Analysis** - Your investigation process
4. **Solution** - Step-by-step walkthrough
5. **Flag** - The captured flag
6. **Lessons Learned** - Key takeaways

## 🏷️ Categories & Tags

### Categories
Use CTF names as categories (e.g., "HTB Cyber Apocalypse 2026")

### Tags
- **Category**: `web`, `pwn`, `crypto`, `reverse`, `forensics`, `misc`
- **Difficulty**: `easy`, `medium`, `hard`, `insane`
- **Technique**: `sqli`, `xss`, `rop`, `rsa`, etc.

## 🚀 Deployment

The site auto-deploys to GitHub Pages on push to `main` branch via GitHub Actions.

### Manual Build

```bash
hugo --gc --minify
```

Output is in the `public/` directory.

## 📜 License

- **Code**: MIT License
- **Writeups**: CC BY-NC-SA 4.0

## 🤝 Contributing

1. Fork the repo
2. Create your writeup branch (`git checkout -b writeup/ctf-challenge`)
3. Write your writeup using the template
4. Commit (`git commit -m 'Add writeup for X'`)
5. Push (`git push origin writeup/ctf-challenge`)
6. Open a Pull Request

---

*Happy hacking!* 🚀
