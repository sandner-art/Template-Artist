# Artist Portfolio - Blogger Template

A clean, minimalist, one-page portfolio template version for Blogger designed for artists and creatives. It features a responsive grid gallery, automatic slideshow, and bilingual support (Czech/English) capabilities.

## 🚀 Features
*   **One-Page Layout:** Smooth scrolling between sections.
*   **Auto-Gallery:** Your Blogger "Posts" automatically populate the "Work" grid.
*   **Easy Editing:** Edit text and images via the Blogger "Layout" tab (no coding required for daily updates).
*   **Responsive:** Looks great on mobile and desktop.
*   **Speed:** Uses standard Blogger infrastructure for fast image loading.

---

## 🛠️ Installation

1.  Download the `theme.xml` file (or copy the full XML code, in this repo it is the file docs\blogger_version\theme_v2.md or theme_vX.md).
2.  Go to your **Blogger Dashboard** > **Theme**.
3.  Click the **Arrow (▼)** next to the "Customize" button.
4.  Select **Edit HTML**.
5.  **Delete everything** currently in the box (Ctrl+A -> Delete).
6.  **Paste** the new template code.
7.  Click the **Save** (Floppy Disk icon) in the top right.

---

## 📸 Image Management (Important!)

Since this is a portfolio, you need a way to host images (like your profile photo or exhibition shots) without them showing up as "Artworks" in your main gallery grid.

**The "Assets Page" Strategy:**
1.  Go to **Pages** > **New Page**.
2.  Title it: `Website Assets - DO NOT DELETE`.
3.  Upload all your static images here (Profile photo, Slideshow images, Studio shots).
4.  **Publish** the page.
5.  Open the published page, right-click an image, and select **Copy Image Address**.
6.  Use this link in your layout widgets.

> **Pro Tip:** In the image link, look for `/s320/` or `/w400/`. Change this number to `/s1600/` to get high-quality images for your headers!

---

## 🎨 Editing Content (The Layout Tab)

Most of your site can be managed via **Blogger Dashboard > Layout**.

### 1. Hero Slideshow (HTML1)
*   **Location:** Layout > Hero Section > HTML1.
*   **Action:** Click **Edit**.
*   **How to change images:** Look for `<img src="...">` tags inside the `hero-slideshow` div. Replace the links with your own from your Assets Page.
*   **How to change text:** Find `<h1>ARTIST NAME</h1>` and change it to your name.

### 2. Selected Works (The Grid)
*   **How it works:** This section is automatic.
*   **To add work:** Simply create a **New Post**.
    *   Upload the artwork image (make sure it is the **first** image in the post).
    *   The Post Title becomes the Artwork Title.
    *   The Post Body text becomes the description/details.
*   **Note:** Do not put "Profile" or "News" photos in Posts, or they will appear in the grid. Use Pages for those.

### 3. Media & Process (HTML2)
*   **Location:** Layout > Static Content Sections > HTML2.
*   **Action:** Click **Edit**.
*   **Content:** This section contains the "Lead text", the "Process" description, the "Quote", and the "Exhibition Image".
*   **Tip:** The text is set up for bilingual support. The first line is Czech (bold), the second is English (italic).

### 4. About Section (HTML3)
*   **Location:** Layout > Static Content Sections > HTML3.
*   **Action:** Click **Edit**.
*   **Content:** Contains the Artist Bio, Portrait Image, and CV/Timeline.
*   **Image:** Replace the `src="..."` link in the `<img>` tag with your portrait link.

### 5. Exhibitions & News (HTML4)
*   **Location:** Layout > Static Content Sections > HTML4.
*   **Action:** Click **Edit**.
*   **Structure:**
    ```html
    <div class="timeline-item">
        <div class="timeline-date">YEAR</div>
        <h3>Exhibition Name</h3>
        <p>Description</p>
        <div class="timeline-location">City/Location</div>
    </div>
    ```
*   **To add a new exhibition:** Copy one complete `timeline-item` block and paste it at the top of the list.

### 6. Contact (HTML5)
*   **Location:** Layout > Static Content Sections > HTML5.
*   **Action:** Click **Edit**.
*   **Content:** Update your email address in the `mailto:` link and your social media links in the `href="#"` tags.

---

## ⚙️ Advanced Customization

### Changing the Menu (Navigation)
The menu links are located in the XML code itself (not the Layout tab).
1.  Go to **Theme > Edit HTML**.
2.  Search (Ctrl+F) for `<div class="nav-links"`.
3.  You will see lines like: `<a href="#work">Work</a>`.
4.  You can change the text or add new links here.

### SEO Settings
1.  Go to **Settings > Basic**.
2.  **Title:** Set your Artist Name.
3.  **Description:** Paste the 500-char bilingual description provided.
4.  **Language:** Set to "Czech" or "English" (this template works with both).

### Changing Colors
To change the site colors (e.g., make the background dark or change the accent color):
1.  Go to **Theme > Edit HTML**.
2.  Search for `:root`.
3.  Change the hex codes for `--bg-primary`, `--text-primary`, etc.

---

## ⚠️ Troubleshooting

*   **"Widget ID is not valid":** If you see this error when saving, ensure you haven't duplicated a widget ID (like having two `Blog1` widgets).
*   **Images are blurry:** Check your image URL. If it says `/s320/`, change it to `/s1600/`.
*   **Post title hidden behind menu:** The CSS is set to `margin-top: 100px` for single posts. If you change the menu height, adjust `.post-page` margin in the CSS.

---

## 🌍 Multilingual Setup (Advanced)

Blogger does not natively support multi-language sites (like WordPress). However, you can create a multilingual experience using one of these two methods.

### Method 1: The Bilingual UI (Recommended)
This is how the template is currently designed. You simply write both languages in the same block, styling the secondary language differently.
*   **Pros:** Easiest to maintain, good for SEO (both languages are visible to Google).
*   **How to do it:**
    ```html
    <p>
        <strong>Czech Text Here</strong><br>
        <span style="font-style: italic; color: #666;">English Translation Here</span>
    </p>
    ```

### Method 2: The CSS Switcher (Clickable EN / CZ)
If you want a button that hides Czech and shows English (and vice versa), follow these steps.

**1. Add CSS to Theme**
Go to **Theme > Edit HTML** and paste this inside the `<b:skin>...</b:skin>` section:
```css
/* Default: Show Czech, Hide English */
.lang-en { display: none; }
.lang-cz { display: inline; }

/* When Body has 'english-mode' class: Hide Czech, Show English */
body.english-mode .lang-cz { display: none; }
body.english-mode .lang-en { display: inline; }
body.english-mode .lang-en-block { display: block; } /* For full paragraphs */
```

**2. Add the Switcher Script**
Paste this just before the closing `</body>` tag in **Theme > Edit HTML**:
```javascript
<script>
function setLanguage(lang) {
    if(lang === 'en') {
        document.body.classList.add('english-mode');
        localStorage.setItem('siteLang', 'en');
    } else {
        document.body.classList.remove('english-mode');
        localStorage.setItem('siteLang', 'cz');
    }
}

// Check saved preference on load
if(localStorage.getItem('siteLang') === 'en') {
    document.body.classList.add('english-mode');
}
</script>
```

**3. Update Your Menu**
In **Theme > Edit HTML**, find the `<div class="nav-links">` section and add these buttons:
```html
<button onclick="setLanguage('cz')" style="cursor:pointer; background:none; border:none;">CZ</button>
<span>|</span>
<button onclick="setLanguage('en')" style="cursor:pointer; background:none; border:none;">EN</button>
```

**4. Write Your Content**
Now, when editing your Widgets (Layout tab) or Posts, wrap your text in these classes:

```html
<!-- Example for About Section -->
<h3>
    <span class="lang-cz">O Mně</span>
    <span class="lang-en">About Me</span>
</h3>

<p>
    <span class="lang-cz">Jsem umělkyně z Teplic...</span>
    <span class="lang-en">I am an artist from Teplice...</span>
</p>
```

### Handling Blog Posts (Gallery)
For the Gallery grid, you cannot easily filter posts by language tag on a one-page site without complex coding.
*   **Best Practice:** Write the post titles and snippets bilingually (e.g., Title: *"Krajina / Landscape"*).
*   **Inside the Post:** You can use the **Method 2** CSS classes inside the post body editor (HTML View) so the description switches language based on the user's selection.