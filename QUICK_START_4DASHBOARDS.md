# Quick Start Guide - 4 Dashboards ⚡

Get up and running with your new 4-dashboard system in 2 minutes!

---

## 🚀 Step 1: Start the Server

Open PowerShell and run:
```powershell
cd C:\Users\adere\Desktop\EBCWIP
python -m http.server 8000 --bind 127.0.0.1
```

You should see:
```
Serving HTTP on 127.0.0.1 port 8000 (http://127.0.0.1:8000/) ...
```

---

## 🌐 Step 2: Open Your Browser

Navigate to:
```
http://localhost:8000/staff-login.html
```

---

## 👤 Step 3: Log In to Your Dashboard

### Manager Dashboard
**Email:** `manager@emilybakes.com`  
**Password:** `test`

**What you'll see:** Complete business overview with revenue tracking and analytics

---

### Baker Dashboard
**Email:** `baker@emilybakes.com`  
**Password:** `test`

**What you'll see:** Daily baking queue with time estimates and special instructions

---

### Decorator Dashboard
**Email:** `decorator@emilybakes.com`  
**Password:** `test`

**What you'll see:** Decoration task list with design preferences and priorities

---

### Sales Dashboard
**Email:** `sales@emilybakes.com`  
**Password:** `test`

**What you'll see:** Sales tracking, targets, and customer metrics

---

## 📊 Your Dashboard Layout

Every dashboard has:

```
[Header with User Info]
[Sidebar Navigation] [Main Content Area]
                      ├─ Summary Cards (KPIs)
                      ├─ Quick Actions
                      ├─ Status Overview
                      ├─ Charts/Tables
                      └─ Details Table
```

---

## 🎯 What Each Dashboard Shows

### 📊 Manager
- 4 Summary Cards: Orders, Today's Orders, Revenue, Customers
- Quick Actions: Create Order, View All, Add Customer, Reports
- Status Overview: 3 status boxes (Baking, Decorating, Ready)
- 3 Interactive Charts
- Recent Orders Table

### 👨‍🍳 Baker
- 3 Summary Cards: Cakes to Bake, Completed, Time Remaining
- Quick Actions: Mark Complete, Add Note, View Schedule
- Status Overview: In Progress, Ready, Completed
- Baking Queue Table
- Special Instructions Section

### ✨ Decorator
- 3 Summary Cards: Cakes to Decorate, Completed, Designs Created
- Quick Actions: Start Decorating, Upload Design, Design Gallery
- Status Overview: In Progress, Ready, Completed
- Decoration Queue Table
- Design Preferences Section

### 💼 Sales
- 4 Summary Cards: Today's Sales, Customers Contacted, Pending, Target
- Quick Actions: Create Order, My Customers, Call Customer, Orders
- Status Overview: Today's Orders, Repeat Customers, Conversion Rate
- 2 Analytics Charts
- Recent Orders Table with Commissions

---

## 🔗 Navigation

### All Dashboards Have
- **Logo** - Click to stay on current page
- **User Badge** - Shows your role and name
- **Sidebar Menu** - Jump between pages quickly
- **Back to Site** - Return to main website
- **Logout** - Sign out and return to login

### Each Dashboard Includes
- Dashboard (Overview)
- Orders/Tasks (Role-specific)
- Additional pages (Customers, Reports, Schedule, etc.)
- Settings (coming soon)

---

## ⚙️ Quick Customizations

### Change Your Dashboard Title
Edit the file and find:
```html
<div class="header-logo">📊 EBC Dashboard</div>
```

Change to whatever you want!

### Add/Remove Navigation Items
Find the sidebar section and add/remove links:
```html
<li><a href="page.html" class="nav-link">🎯 New Page</a></li>
```

### Change Colors
Edit `dashboard/css/dashboard-improved.css` and update:
```css
--primary: #C44569;  /* Your color here */
```

---

## 📁 Files You Can Edit

```
✏️ manager-dashboard.html        (Manager specific)
✏️ baker-dashboard.html          (Baker specific)
✏️ decorator-dashboard.html      (Decorator specific)
✏️ sales-dashboard.html          (Sales specific)
✏️ css/dashboard-improved.css    (All styling)
✏️ staff-login.html              (Login page)
```

**Don't edit:**
- `js/main.js` (shared functions)
- Old dashboard files (they're legacy)

---

## 🎨 UX Features

All dashboards include:
- ✅ Modern gradient buttons
- ✅ Smooth hover effects
- ✅ Emoji icons for quick scanning
- ✅ Color-coded status indicators
- ✅ Responsive design (works on mobile)
- ✅ Interactive charts (Manager & Sales only)
- ✅ Professional table styling
- ✅ Easy-to-use sidebar navigation

---

## 📱 Mobile Access

Dashboards work great on:
- ✅ Desktop computers
- ✅ Tablets (iPad, Android)
- ✅ Smartphones (iPhone, Android)

The layout automatically adjusts to fit your screen size!

---

## 🔒 Security Notes

- Passwords are currently `test` (change in `staff-login.html` for production)
- Session data stored in localStorage (not encrypted - for demo only)
- Always use HTTPS in production
- Implement proper authentication backend

---

## 📞 Support Customization

For further customizations, see:
- `HOW_TO_CUSTOMIZE_DASHBOARDS.md` - Detailed guide
- `DASHBOARDS_UX_COMPARISON.md` - Design details
- `DASHBOARDS_CREATED.md` - Full feature list

---

## 🎯 Next Steps

1. ✅ Test each dashboard by logging in as different roles
2. ✅ Explore the navigation and features
3. ✅ Customize colors/styling if desired
4. ✅ Add new pages by copying template HTML
5. ✅ Connect to real backend data
6. ✅ Deploy to production

---

## ✨ Summary

You now have:
- ✅ 4 professional, role-based dashboards
- ✅ Improved UX with modern design
- ✅ Automatic role-based routing
- ✅ Fully responsive design
- ✅ Easy-to-customize code
- ✅ Complete documentation

**Everything is ready to go!**

🎉 Start testing now at `http://localhost:8000/staff-login.html`
