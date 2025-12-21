# Template-Artist
Test template for artist/designer/photographer presentation.

Here is the solution broken down into two parts: how to structure your files for GitHub Pages, and the code snippet to replace your current text buttons with clean, minimal SVG icons.

### GitHub Pages Folder Structure

For a clean repository, do not dump all images in the root folder. The standard convention is to create an `assets` folder.

**Recommended Structure:**
```text
my-portfolio-repo/
├── index.html          <-- Your main HTML file (must be named index.html)
└── assets/
    ├── images/         <-- Put all your .jpg and .png files here
    │   ├── profile.jpg
    │   ├── sculpture-1.jpg
    │   └── hero-bg.jpg
    └── css/            <-- (Optional) If you ever separate your CSS
```

**How to link them in your HTML:**
When your images are in that folder, you change the `src` attribute in your HTML code from the Unsplash links to relative paths:

```html
<!-- BEFORE -->
<img src="https://images.unsplash.com/..." alt="...">

<!-- AFTER -->
<img src="assets/images/sculpture-1.jpg" alt="Sculpture 1">
```

---
