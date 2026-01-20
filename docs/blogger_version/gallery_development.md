# Questions and Gallery Gadget

### 1. Can I add other gadgets?
**Yes.** You can go to the **Layout** tab and click "Add a Gadget" in any available section.
*   **Safe to add:** HTML/JavaScript, Text, Image, Contact Form, Profile.
*   **Where to put them:** You can place them in the existing sections. If you need a completely new area (e.g., a Sidebar), you would need to edit the HTML to create a new `<b:section>`.

### 2. Can I duplicate the Gallery Gadget?
**No.** This is a hard restriction in Blogger.
*   You are allowed **only one** widget of type "Blog" (`Blog1`) per template.
*   If you try to add a second one, Blogger will give you an error.

### 3. Can I sort posts by tags (e.g., Sculptures vs. Paintings)?
**Yes!** This is the standard way to handle portfolios.

Instead of creating *separate* grids (which requires the impossible second Blog widget), the best solution is to use **JavaScript Filtering**.

You will modify your code so that:
1.  All your work loads in the main grid.
2.  We add buttons at the top: **All | Sculptures | Paintings | Drawings**.
3.  When you click a button, the grid instantly shuffles to show only that category.

Here is the code change to make this work.

---

### Step 1: Update the Blog Widget (Theme > Edit HTML)

We need to tell the template to print the **Labels (Tags)** inside the HTML of each gallery item so JavaScript can find them.

Find your `Blog1` widget code (search for `id='Blog1'`). Look for the loop where the `<div class="gallery-item">` starts.

**Replace the entire `<b:loop>` block with this upgraded version:**

```xml
<b:loop values='data:posts' var='post'>
    <!-- We add the labels as CSS classes to the div -->
    <div expr:class='"gallery-item " + data:post.labels map (l => l.name) join " "'>
        <a expr:href='data:post.url'>
            <b:if cond='data:post.featuredImage'>
                <img expr:alt='data:post.title' expr:src='data:post.featuredImage'/>
            <b:else/>
                <img alt='No image' src='https://via.placeholder.com/600x750?text=No+Image'/>
            </b:if>
            <div class="gallery-item-info">
                <h3><data:post.title/></h3>
                <p><b:eval expr='snippet(data:post.body, {length: 50, links: false})'/></p>
                
                <!-- Optional: Show tags in the hover text -->
                <div class="post-tags" style="font-size:0.7rem; text-transform:uppercase; opacity:0.7; margin-top:5px;">
                    <b:loop values='data:post.labels' var='label'>
                        <span style="margin-right:5px;">#<data:label.name/></span>
                    </b:loop>
                </div>
            </div>
        </a>
    </div>
</b:loop>
```

### Step 2: Add Filter Buttons (Layout Tab)

We need buttons to control the filter. We will add them via the **HTML1 (Hero Slideshow)** widget or just manually place them in the code right above the Grid in the **HTML**.

**Best Approach:** Edit the XML HTML directly to place the buttons exactly where the "Columns" buttons are.

Search for `<div class="gallery-controls">` in your HTML.
**Replace that whole container with this:**

```html
<div class="gallery-controls-wrapper" style="margin-bottom: 2rem; text-align: center;">
    
    <!-- CATEGORY FILTER BUTTONS -->
    <div class="filter-controls" style="margin-bottom: 1rem;">
        <button class="filter-btn active" onclick="filterGallery('all', this)">All</button>
        <!-- Replace these with your actual Label names exactly as they are on your posts -->
        <button class="filter-btn" onclick="filterGallery('Sculptures', this)">Sculptures</button>
        <button class="filter-btn" onclick="filterGallery('Paintings', this)">Paintings</button>
        <button class="filter-btn" onclick="filterGallery('Drawings', this)">Drawings</button>
    </div>

    <!-- GRID LAYOUT BUTTONS (Keep existing) -->
    <div class="layout-controls" style="display:inline-flex; gap:0.5rem; opacity:0.6; transform:scale(0.9);">
        <button class="grid-toggle" onclick="setGridLayout(2)">2 Col</button>
        <button class="grid-toggle active" onclick="setGridLayout(3)">3 Col</button>
        <button class="grid-toggle" onclick="setGridLayout(4)">4 Col</button>
    </div>

</div>
```

### Step 3: Add the CSS & JS

**1. CSS:** Add this to your `<b:skin>`:
```css
.filter-btn {
    padding: 0.5rem 1.2rem;
    margin: 0 0.25rem;
    background: transparent;
    border: 1px solid var(--border);
    border-radius: 20px;
    cursor: pointer;
    color: var(--text-primary);
    transition: all 0.3s ease;
}

.filter-btn:hover, .filter-btn.active {
    background: var(--text-primary);
    color: var(--bg-primary);
    border-color: var(--text-primary);
}

/* Animation for filtering */
.gallery-item {
    transition: all 0.4s ease;
}
.gallery-item.hide {
    display: none; /* Hides items that don't match */
}
```

**2. JavaScript:** Add this to the bottom `<script>` section:
```javascript
function filterGallery(category, btn) {
    // 1. Manage Active Button State
    const buttons = document.querySelectorAll('.filter-btn');
    buttons.forEach(b => b.classList.remove('active'));
    btn.classList.add('active');

    // 2. Filter The Items
    const items = document.querySelectorAll('.gallery-item');
    
    items.forEach(item => {
        if (category === 'all') {
            item.classList.remove('hide');
        } else {
            // Check if the item has the class name matching the category
            if (item.classList.contains(category)) {
                item.classList.remove('hide');
            } else {
                item.classList.add('hide');
            }
        }
    });
}
```

### How to use it:
1.  Create a post.
2.  In the **Labels** (Tags) setting on the right side of the post editor, type `Sculptures` (or whatever category you want).
3.  **Important:** The Label name in the post must match the Button name in the code exactly (Case Sensitive). If the label is "Sculptures", the button onclick must be `filterGallery('Sculptures', this)`.