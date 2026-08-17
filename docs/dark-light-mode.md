# 🌓 Dark & Light Mode Compatibility Guide

A major flaw in older GitHub profile README tutorials is that images, badges, and stat cards are hardcoded to a single color scheme. When a user switches themes on GitHub (between Light, Dark, and Dark Dimmed), static banners or text can become completely illegible.

Here is how to make your GitHub profile dynamically adapt to the user's active theme.

---

## 1. Using HTML `<picture>` with `prefers-color-scheme` (Recommended)

GitHub's Markdown renderer natively supports the standard HTML `<picture>` element with CSS media queries.

```html
<picture>
  <!-- Dark mode image -->
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=YOUR_USER&theme=tokyonight&hide_border=true" />
  
  <!-- Light mode image -->
  <source media="(prefers-color-scheme: light)" srcset="https://github-readme-stats.vercel.app/api?username=YOUR_USER&theme=default&hide_border=true" />
  
  <!-- Fallback image -->
  <img alt="GitHub Stats" src="https://github-readme-stats.vercel.app/api?username=YOUR_USER&hide_border=true" />
</picture>
```

---

## 2. Using GitHub Markdown Theme Fragments (`#gh-dark-mode-only` & `#gh-light-mode-only`)

For standard Markdown image syntax (`![alt](url)`), GitHub supports URL hash fragments:

```markdown
<!-- Visible only in Dark Theme -->
![Header Dark](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=2,3,5&height=180&text=Welcome#gh-dark-mode-only)

<!-- Visible only in Light Theme -->
![Header Light](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=24,28,30&height=180&text=Welcome#gh-light-mode-only)
```

---

## 3. SkillIcons.dev Theme Switching

If you use [skillicons.dev](https://skillicons.dev), you can dynamically adjust theme per mode using `<picture>`:

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://skillicons.dev/icons?i=ts,react,nextjs,nodejs,go,docker,postgres&theme=dark" />
  <source media="(prefers-color-scheme: light)" srcset="https://skillicons.dev/icons?i=ts,react,nextjs,nodejs,go,docker,postgres&theme=light" />
  <img src="https://skillicons.dev/icons?i=ts,react,nextjs,nodejs,go,docker,postgres" alt="Skill Icons" />
</picture>
```

---

## 4. Snake Contribution Graph Theme Switching

When generating the snake animation via GitHub Actions, output both light and dark SVGs:

```yaml
outputs: |
  dist/github-snake.svg
  dist/github-snake-dark.svg?palette=github-dark
```

Then display them adaptively:

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-snake.svg" />
  <img alt="Snake Game Graph" src="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-snake.svg" width="100%" />
</picture>
```
