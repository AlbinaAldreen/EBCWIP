# Testing Checklist - Emily Bakes Cakes Manager Dashboard

Use this checklist to verify all features are working correctly.

## 🚀 Setup & Loading

- [ ] Navigate to `emily_bakes_staff/index.html` in browser
- [ ] Dashboard loads without errors
- [ ] Page displays in under 1 second
- [ ] All fonts and colors load correctly
- [ ] No console errors (check with F12)

## 🎨 Header

- [ ] Manager role badge displays "Manager"
- [ ] Manager name displays "Emily Boudreaux"
- [ ] Pickup badge shows correct number (e.g., "2 pickups today")
- [ ] "Back to Site" button is visible and clickable
- [ ] "Logout" button is visible and clickable (shows alert)

## 📊 Summary Cards

- [ ] 4 summary cards display (Pending Pickups, Today's Orders, Weekly Revenue, New Customers)
- [ ] Card numbers are populated with data (not 0)
- [ ] "View Details →" links are clickable
- [ ] Links navigate to correct pages:
  - [ ] Pending Pickups → pending_pickups.html
  - [ ] Today's Orders → todays_orders.html
  - [ ] Weekly Revenue → reports.html
  - [ ] New Customers → customers.html

## 🎯 Quick Action Buttons

- [ ] All 6 buttons display
- [ ] Buttons are laid out in grid
- [ ] "Create New Order" button shows alert
- [ ] "View All Orders" button navigates to orders.html
- [ ] "Add Customer" button shows alert
- [ ] "Find Customer" button shows alert
- [ ] "Financial Reports" button navigates to reports.html
- [ ] "Print Daily Summary" button shows alert

## 📦 Status Overview

- [ ] 3 status boxes display (Pending Baking, Pending Decorating, Ready for Pickup)
- [ ] Numbers are populated (not 0)
- [ ] Colors are correct (amber, purple, green)
- [ ] Labels are clearly visible

## 📈 Charts

### Today's Order Status (Pie Chart)
- [ ] Chart displays without errors
- [ ] Chart has colors and legend
- [ ] Legend shows status labels (To Be Created, In Baking, etc.)
- [ ] Chart updates with current day's data

### Top Selling Products (Horizontal Bar Chart)
- [ ] Chart displays as horizontal bars
- [ ] Shows up to 5 products
- [ ] Product names are visible
- [ ] Bars are proportional to order counts

### Quarterly Revenue (Bar Chart)
- [ ] Chart displays as vertical bars
- [ ] Shows Q1, Q2, Q3, Q4
- [ ] Y-axis shows currency ($)
- [ ] Bars reflect actual revenue data

## 📋 Today's Pickups Table

- [ ] Table displays with 6 columns: Time, Order ID, Customer, Cake, Status, Total, Action
- [ ] Table has 5-6 rows of data
- [ ] Pickups are sorted by time
- [ ] Status badges have correct colors
- [ ] Totals display in currency format ($)
- [ ] "View" links are clickable

## 📅 Tomorrow's Schedule

- [ ] Schedule items display with Time, Customer, Summary
- [ ] At least 4 items show
- [ ] Times are formatted correctly (e.g., "10:00 AM")
- [ ] Customer names are visible
- [ ] Summaries are descriptive

## 🧭 Left Navigation

- [ ] Sidebar displays with 5 links (Dashboard, Orders, Customers, Reports, Settings)
- [ ] Dashboard link is highlighted/active
- [ ] All links are clickable
- [ ] Hover effect on links (color change, background)

## 📍 Pending Pickups Page (pending_pickups.html)

- [ ] Page loads with same header and sidebar
- [ ] "Pending Pickups" title displays
- [ ] Date shows correctly (e.g., "Today — Friday, November 21, 2025")
- [ ] Navigation link is marked as "active"

### Search & Filter
- [ ] Search input field displays
- [ ] Status filter dropdown displays (All, Ready, Not Ready)
- [ ] Results count displays (e.g., "6 results")
- [ ] Search works - typing filters table in real-time
- [ ] Filter dropdown works - changes displayed rows
- [ ] Searching by Order ID works (e.g., "ORD-001")
- [ ] Searching by Customer name works
- [ ] Searching by Phone works

### Table Content
- [ ] Table has 7 columns: Order ID, Customer, Phone, Pickup Time, Status, Total, Action
- [ ] All pickups for today display
- [ ] Status badges have correct colors
- [ ] "View" buttons are clickable

## 📅 Today's Orders Page (todays_orders.html)

- [ ] Page loads with same header and sidebar
- [ ] "Today's Orders" title displays
- [ ] Date displays correctly
- [ ] Navigation link is marked as "active"

### Search & Filter
- [ ] Search input field displays
- [ ] Status filter dropdown displays (All, To Be Created, In Baking, Decorating, Ready, Picked Up)
- [ ] Results count displays
- [ ] Search works by Order ID, Customer, Cake Type
- [ ] Filter dropdown works correctly
- [ ] Multiple filter options work

### Table Content
- [ ] Table has 8 columns: Order ID, Customer, Order Time, Pickup Date, Status, Layers, Total, Action
- [ ] All today's orders display
- [ ] Layers column shows correct numbers (2-4)
- [ ] "View" buttons are clickable

## 🔗 Navigation Between Pages

- [ ] Can navigate from Dashboard → Pending Pickups
- [ ] Can navigate from Dashboard → Today's Orders
- [ ] Can navigate from Pending Pickups → Dashboard
- [ ] Can navigate from Today's Orders → Dashboard
- [ ] "Back to Site" button works from all pages (shows alert)
- [ ] Sidebar navigation works on all pages
- [ ] Active page is highlighted in sidebar

## 📱 Responsive Design

### Desktop (1200px+)
- [ ] Cards display in 4-column grid
- [ ] Charts are side-by-side
- [ ] Tables are fully visible
- [ ] Sidebar is visible at 220px width

### Tablet (768px-1200px)
- [ ] Cards adjust to 2-3 columns
- [ ] Charts stack vertically
- [ ] Tables are readable
- [ ] Sidebar is visible

### Mobile (<768px)
- [ ] Cards stack to single column
- [ ] Charts stack vertically
- [ ] Tables are scrollable horizontally
- [ ] Sidebar may be hidden/collapsed (design dependent)
- [ ] Layout is still functional

### Test Responsiveness
- [ ] Resize browser window from desktop → mobile
- [ ] Use DevTools (F12) → Toggle device toolbar
- [ ] Test on actual mobile device if possible

## 🎨 Visual Polish

- [ ] Colors match brand (raspberry #C44569, cream #FAF5F0, etc.)
- [ ] Fonts are readable and consistent
- [ ] Spacing and padding look balanced
- [ ] Shadows are subtle and professional
- [ ] Buttons have hover effects
- [ ] Links are visibly different from text
- [ ] Status badges are color-coded and clear

## 🔧 Data Accuracy

- [ ] Pending Pickup count matches "Ready" orders for today
- [ ] Today's Orders count includes all today's orders
- [ ] Weekly Revenue is sum of "Picked Up" orders (last 7 days)
- [ ] New Customers count matches customers created this week
- [ ] Status boxes show correct distribution
- [ ] Charts display correct data

### Verify Sample Data
- [ ] 6 orders for today are displayed
- [ ] Various statuses are represented (To Be Created, In Baking, Decorating, Ready, Picked Up)
- [ ] Customer names match between orders and schedule
- [ ] Phone numbers are formatted correctly
- [ ] Prices are in currency format ($X.XX)

## 📊 Chart Interactivity

- [ ] Hover over pie chart → shows tooltip with count
- [ ] Hover over bar charts → shows values
- [ ] Charts fit in container (not overflowing)
- [ ] Legends are clickable to hide/show segments
- [ ] Charts are readable on small screens

## 🔍 Browser Compatibility

- [ ] Works in Chrome 90+
- [ ] Works in Firefox 88+
- [ ] Works in Edge 90+
- [ ] Works in Safari 14+ (if on Mac)
- [ ] Works in mobile browsers

## 🚫 Error Handling

- [ ] No JavaScript errors in console (F12)
- [ ] No 404 errors for missing files
- [ ] Search with no results shows empty table
- [ ] Filter with no matches shows empty table
- [ ] Charts display even if no data

## ✨ Extra Features

- [ ] Placeholder pages (Orders, Customers, Reports, Settings) display correctly
- [ ] Placeholder pages have "Feature Coming Soon" message
- [ ] Placeholder pages maintain same header/sidebar structure
- [ ] All placeholder pages are navigable

## 🎯 Performance

- [ ] Page loads in under 1 second
- [ ] Charts render in under 500ms
- [ ] Search results appear instantly (<50ms)
- [ ] Filters update immediately
- [ ] No noticeable lag or stuttering
- [ ] Smooth animations and transitions

## 📝 Placeholder Pages

### Orders Page (orders.html)
- [ ] Loads with correct header
- [ ] Shows "Feature Coming Soon" message
- [ ] Navigation to/from page works

### Customers Page (customers.html)
- [ ] Loads with correct header
- [ ] Shows "Feature Coming Soon" message
- [ ] Navigation to/from page works

### Reports Page (reports.html)
- [ ] Loads with correct header
- [ ] Shows "Feature Coming Soon" message
- [ ] Navigation to/from page works

### Settings Page (settings.html)
- [ ] Loads with correct header
- [ ] Shows "Feature Coming Soon" message
- [ ] Navigation to/from page works

## 🎉 Final Checks

- [ ] No broken images or missing assets
- [ ] No console warnings or errors
- [ ] All links work correctly
- [ ] All buttons are functional
- [ ] All pages load properly
- [ ] Responsive design works smoothly
- [ ] Data is accurate and complete
- [ ] Documentation is clear and helpful

---

## Testing Notes

### Quick Test Path
1. Open index.html
2. Check dashboard displays with data
3. Navigate to pending_pickups.html
4. Test search and filter
5. Navigate to todays_orders.html
6. Test search and filter
7. Check placeholder pages
8. Resize browser to test responsiveness

### Full Test Duration
- Approximately 10-15 minutes for complete testing
- 5 minutes for quick test

### Common Issues
- **Charts not showing**: Check browser console for errors, verify Chart.js CDN is accessible
- **Data not displaying**: Refresh page, check browser console
- **Layout broken**: Check CSS file is linked correctly
- **Mobile issues**: Test in actual DevTools device emulation

---

**All tests should pass before considering the project ready for use.**

✅ **When all checkboxes are marked, the dashboard is ready for production!**
