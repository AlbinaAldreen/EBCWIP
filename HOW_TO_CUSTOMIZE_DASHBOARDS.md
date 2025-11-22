# How to Edit & Customize Your Dashboards 🎨

Each dashboard is fully customizable and independent. You can edit them individually without affecting others.

---

## File Locations

```
EBCWIP/
└── dashboard/
    ├── manager-dashboard.html       ← Edit Manager Dashboard
    ├── baker-dashboard.html         ← Edit Baker Dashboard
    ├── decorator-dashboard.html     ← Edit Decorator Dashboard
    ├── sales-dashboard.html         ← Edit Sales Dashboard
    ├── css/
    │   ├── dashboard-improved.css   ← Edit Design/Styling
    │   └── styles.css               ← Legacy (don't use)
    └── js/
        └── main.js                  ← Shared Functions
```

---

## Quick Edits Guide

### Change the Title/Logo
In any dashboard HTML file, find:
```html
<div class="header-logo">📊 EBC Dashboard</div>
```

Change to:
```html
<div class="header-logo">🏪 Emily Bakes Cakes</div>
```

### Change the Page Title
Find:
```html
<h1 class="page-title">Welcome to Dashboard</h1>
<p class="page-subtitle">Overview of your bakery operations</p>
```

Change to:
```html
<h1 class="page-title">Your Custom Title</h1>
<p class="page-subtitle">Your custom subtitle</p>
```

### Add/Remove Summary Cards
Each dashboard has a `summary-grid` section:
```html
<div class="summary-grid">
    <div class="summary-card">
        <div class="card-icon">📊</div>
        <div class="card-number" id="metric-id">0</div>
        <div class="card-label">Card Title</div>
        <a href="page.html" class="card-action">View Details →</a>
    </div>
    <!-- Copy this div to add more cards -->
</div>
```

**To add a new card:**
1. Copy the entire `<div class="summary-card">` block
2. Paste it after the last card
3. Change the icon emoji
4. Change the label text
5. Update the `id` in `card-number` div
6. Add JavaScript to populate it (see below)

**To remove a card:**
Simply delete the entire `<div class="summary-card">` block.

### Change Navigation Links
Find the sidebar navigation:
```html
<nav class="nav-sidebar">
    <ul>
        <li><a href="manager-dashboard.html" class="nav-link active">
            📊 Dashboard
        </a></li>
        <li><a href="manager-orders.html" class="nav-link">
            📋 Orders
        </a></li>
        <!-- More links -->
    </ul>
</nav>
```

**To add a new navigation item:**
```html
<li><a href="new-page.html" class="nav-link">
    🎯 New Page
</a></li>
```

**To remove a navigation item:**
Delete the entire `<li>` element.

### Change Quick Action Buttons
Find the action buttons section:
```html
<div class="action-buttons">
    <button class="action-btn-primary" onclick="alert('Action')">
        ➕ New Order
    </button>
</div>
```

**To change button text/action:**
```html
<button class="action-btn-primary" onclick="yourFunction()">
    🎯 Your Button Text
</button>
```

**To make it a link instead:**
```html
<a href="page.html" class="action-btn-primary">
    🔗 Your Link Text
</a>
```

---

## Styling Customizations

All styling is in `dashboard/css/dashboard-improved.css`

### Change the Primary Color
Find at the top:
```css
:root {
    --primary: #C44569;  ← Change this
    --primary-light: #D45579;
    --primary-dark: #A23556;
    /* ... more colors */
}
```

Change to your color (any hex value):
```css
--primary: #FF6B6B;  /* Red */
--primary: #4ECDC4;  /* Teal */
--primary: #95E1D3;  /* Mint */
```

### Change the Background Color
```css
--background: #F8F7F6;  ← Change this
```

### Change Font Sizes
Find any element and change the size:
```css
.page-title {
    font-size: 32px;  ← Change this
}
```

### Add/Change Spacing
```css
.main-content {
    padding: 40px;  ← Change this
}

.summary-grid {
    gap: 24px;  ← Change this
}
```

### Modify Button Styling
```css
.action-btn-primary {
    background: linear-gradient(135deg, var(--primary), var(--primary-light));
    color: white;
    border: none;
    padding: 14px 24px;  ← Change padding
    border-radius: 10px;  ← Change roundness
    font-size: 14px;  ← Change font size
}
```

---

## JavaScript Customizations

Each dashboard has role-specific functions at the bottom.

### Update Summary Card Values
In any dashboard's script section:
```javascript
document.getElementById('pending-pickup-count').textContent = 5;
document.getElementById('weekly-revenue').textContent = '$1,250.00';
```

### Add New Summary Card JavaScript
```javascript
// When a new card element is added with id="my-metric"
document.getElementById('my-metric').textContent = calculateMyMetric();

function calculateMyMetric() {
    // Your calculation here
    return result;
}
```

### Update Status Box Values
```javascript
document.getElementById('status-baking').textContent = 3;
document.getElementById('status-decorating').textContent = 5;
document.getElementById('status-ready').textContent = 2;
```

### Populate Tables Dynamically
Find the table population function:
```javascript
function populateRecentOrders() {
    const orders = getTodaysOrders().slice(0, 5);
    const tbody = document.getElementById('recent-orders');
    tbody.innerHTML = '';

    orders.forEach(order => {
        const row = document.createElement('tr');
        row.innerHTML = `
            <td>#${order.id}</td>
            <td>${order.customerName}</td>
            <td>${order.amount}</td>
            <!-- Add more columns -->
        `;
        tbody.appendChild(row);
    });
}
```

### Modify Chart Data
Find the chart initialization:
```javascript
function initializeCharts() {
    const ctx1 = document.getElementById('todaysStatusChart').getContext('2d');
    
    new Chart(ctx1, {
        type: 'doughnut',
        data: {
            labels: ['Baking', 'Decorating', 'Ready'],
            datasets: [{
                data: [5, 3, 2],  ← Change these numbers
                backgroundColor: ['#F59E0B', '#A855F7', '#10B981'],
            }]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                legend: { position: 'bottom' }
            }
        }
    });
}
```

---

## Create New Dashboard Pages

To create a new page for a dashboard:

1. **Copy an existing HTML file** (e.g., `manager-orders.html`)
2. **Rename it** to match your dashboard (e.g., `baker-inventory.html`)
3. **Update the navigation links** in the main dashboard to point to it
4. **Customize the content** as needed

Example template:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title - Emily Bakes Cakes</title>
    <link rel="stylesheet" href="css/dashboard-improved.css">
</head>
<body>
    <!-- Copy header from any dashboard -->
    <header class="header">
        <!-- ... -->
    </header>

    <!-- Copy sidebar from any dashboard -->
    <nav class="nav-sidebar">
        <!-- ... -->
    </nav>

    <!-- Main content -->
    <main class="main-content">
        <div class="content">
            <div class="page-header">
                <h1 class="page-title">Your Page Title</h1>
                <p class="page-subtitle">Your page description</p>
            </div>
            
            <!-- Your content here -->
        </div>
    </main>

    <script src="js/main.js"></script>
    <script>
        // Your page-specific code here
        document.addEventListener('DOMContentLoaded', () => {
            if (!checkAuthentication()) return;
            updateHeaderWithUserInfo();
            initializeNav();
            // Your initialization code
        });
    </script>
</body>
</html>
```

---

## Common Customizations

### Change Card Color Scheme
Modify the status box CSS:
```css
.status-box.baking {
    border-color: var(--warning);  ← Change color variable
    background: linear-gradient(135deg, rgba(245, 158, 11, 0.05), rgba(245, 158, 11, 0.02));
}
```

### Add More Navigation Items
```html
<li><a href="your-page.html" class="nav-link">
    📌 Your Label
</a></li>
```

### Modify Card Styling
```css
.summary-card {
    background: var(--surface);
    border: 1px solid var(--border-light);
    border-radius: 12px;  ← Adjust roundness
    padding: 28px;  ← Adjust spacing
    cursor: pointer;
    transition: var(--transition);
}
```

### Change Responsive Breakpoints
Find in CSS:
```css
@media (max-width: 1024px) {
    /* Tablet adjustments */
}

@media (max-width: 640px) {
    /* Mobile adjustments */
}
```

---

## Best Practices

✅ **Keep navigation consistent** across all dashboards  
✅ **Use the same color scheme** from CSS variables  
✅ **Match button/card styling** to existing patterns  
✅ **Test on mobile** after making changes  
✅ **Keep file names descriptive** (e.g., `baker-inventory.html`)  
✅ **Comment your custom code** for future reference  
✅ **Don't edit `js/main.js`** unless you know what you're doing  
✅ **Always include authentication check** in new pages  

---

## Troubleshooting

### Dashboard won't load?
- Check browser console for errors (F12)
- Verify file paths are correct
- Ensure `main.js` is linked properly
- Check if stylesheets are loading

### Cards not updating?
- Verify the HTML `id` matches your JavaScript
- Check that your data source is providing values
- Look at browser console for errors

### Styling looks wrong?
- Clear browser cache (Ctrl+Shift+Del)
- Check if CSS file is loading (F12 → Network)
- Verify CSS class names match HTML elements
- Check for CSS conflicts

### Navigation not working?
- Verify file paths in href attributes
- Check that files exist in dashboard folder
- Ensure file names are exact (case-sensitive)

---

## Tips & Tricks

💡 Use emoji in button text for quick visual scanning  
💡 Adjust padding in CSS variables for consistent spacing  
💡 Use data attributes to pass info between pages  
💡 Leverage existing functions in `main.js`  
💡 Test changes in browser before committing  

---

Each dashboard is yours to customize! Start with small changes and work your way up to larger customizations.

**Happy customizing! 🎨**
