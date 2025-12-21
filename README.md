# Template-Artist

A clean, minimalist, and responsive portfolio template designed for artists, designers, and photographers. Built with raw HTML, CSS, and JavaScript—no frameworks or build steps required.

## Features

*   **Minimalist Design:** Focuses entirely on the artwork with a clean typography hierarchy.
*   **Dark/Light Mode:** Automatic theme detection with a manual toggle switch.
*   **Dynamic Gallery:** Grid controls to switch between 2, 3, or 4 columns instantly.
*   **Media Embeds:** Privacy-friendly YouTube embeds (No-Cookie) and minimal SVG social media cards.
*   **Responsive:** Fully optimized for mobile, tablet, and desktop screens.
*   **SEO Ready:** Includes structured data (Schema.org) and meta tags.

Planned: **Multi-Language Support (WIP):** Built-in JSON-based translation system (EN, CS, DE) without a backend.

## Folder Structure & Setup

To keep the repository clean, this template uses a dedicated `assets` folder. Do not dump all images in the root directory.

**Recommended Structure:**
```text
my-portfolio-repo/
├── index.html          <-- Your main HTML file
└── assets/
    ├── images/         <-- Put all your .jpg and .png files here
    │   ├── profile.jpg
    │   ├── sculpture-1.jpg
    │   └── hero-bg.jpg
    └── css/            <-- (Optional) If you decide to separate CSS later
```

### Linking Images
When your images are in the assets folder, update the `src` attribute in your HTML to point to the relative path:

```html
<!-- Example -->
<img src="assets/images/yourartname.jpg" alt="Sculpture 1">
```

## 🚀 How to Use

### 1. Installation
Simply clone this repository or download the ZIP file.
```bash
git clone https://github.com/yourusername/Template-Artist.git
```

### Customizing Content
Because this template uses a translation system, **do not edit the text directly in the HTML elements** (e.g., inside `<h2>`). Instead, edit the JavaScript object at the bottom of `index.html`.

**To change text:**
Scroll to the `<script>` tag and find the `translations` object:
```javascript
const translations = {
    en: {
        "hero.subtitle": "Your Custom Subtitle Here",
        "about.bio1": "Your English bio text...",
        // ...
    },
    cs: {
       // Czech translations...
    }
};
```

### 3. Customizing Social Icons
The template uses inline SVGs for social icons to keep the design minimal (no external font libraries). To change the links, look for the `.social-links` section in the HTML:
```html
<a href="https://instagram.com/YOURHANDLE" ...>
    <svg>...</svg>
</a>
```

### 4. YouTube Embeds
To prevent "Error 153" and respect user privacy, use the `youtube-nocookie` domain in your iframe `src`:
```html
src="https://www.youtube-nocookie.com/embed/VIDEO_ID"
```

## Hosting on GitHub Pages

1.  Upload your files to a GitHub repository.
2.  Go to **Settings** > **Pages**.
3.  Under **Branch**, select `main` (or `master`) and `/root`.
4.  Click **Save**. Your site will be live at `https://yourusername.github.io/Template-Artist/`.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
