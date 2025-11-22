# Emily Bakes Cakes - Manager Dashboard

A complete manager dashboard system built with pure HTML, CSS, and Vanilla JavaScript. No backend required—everything runs as static files in your browser.

## 📁 Project Structure

```
emily_bakes_staff/
├── index.html              # Main Dashboard
├── pending_pickups.html    # Detailed pending pickups page
├── todays_orders.html      # Detailed today's orders page
├── orders.html             # Placeholder
├── customers.html          # Placeholder
├── reports.html            # Placeholder
├── settings.html           # Placeholder
├── css/
│   └── styles.css          # All styling
└── js/
    └── main.js             # All data + dynamic logic
```

## 🚀 Quick Start

1. **Open in Browser**: Simply open `index.html` in any modern web browser
2. **No Installation**: No npm, no Python, no backend needed
3. **Works Offline**: Everything is loaded locally

## 📊 Features

### Dashboard (index.html)
- **Summary Cards**: Pending pickups, today's orders, weekly revenue, new customers
- **Quick Action Buttons**: Create order, view orders, add/find customers, financial reports, print summary
- **Status Overview**: Real-time counts for pending baking, pending decorating, ready for pickup
- **Interactive Charts** (using Chart.js):
  - Today's Order Status (Pie chart)
  - Top Selling Products (Horizontal bar chart)
  - Quarterly Revenue Comparison (Bar chart)
- **Today's Pickups Table**: Sortable, searchable with 6 sample rows
- **Tomorrow's Schedule Preview**: 4 preview events

### Pending Pickups (pending_pickups.html)
- **Full Pickup List**: All pickups for today
- **Search**: By Order ID, Customer name, or phone number
- **Filter**: View all, ready only, or not ready
- **Dynamic Table**: Real-time result count

### Today's Orders (todays_orders.html)
- **Full Order List**: All orders placed for today
- **Search**: By Order ID, Customer, or Cake Type
- **Status Filter**: Filter by status (To Be Created, In Baking, Decorating, Ready, Picked Up)
- **Dynamic Table**: Shows order details including layers and total

### Additional Pages
- **Orders**: Placeholder for future development
- **Customers**: Placeholder for future development
- **Reports**: Placeholder for future development
- **Settings**: Placeholder for future development

## 📊 Data Model

All data is stored in `js/main.js` and includes:

### Orders
Each order contains:
- Order ID
- Customer name & phone
- Order time & pickup time
- Cake type & layers
- Total price
- Status (To Be Created, In Baking, Decorating, Ready, Picked Up)

### Customers
Each customer contains:
- Customer ID
- Name, phone, email
- List of order IDs
- Account creation date

### Schedule
Tomorrow's schedule with time, customer, and order summary

## 🔧 Key JavaScript Functions

### Computed Functions
- `getTodaysOrders()` - Get all orders for today
- `getPendingPickups()` - Get orders ready for pickup
- `getPendingPickupCount()` - Count pending pickups
- `getWeeklyRevenue()` - Calculate 7-day revenue
- `getNewCustomersThisWeek()` - Get new customers this week
- `getStatusCounts()` - Get counts by status
- `getTopProductsThisWeek()` - Get top 5 selling cakes
- `getTodaysStatusBreakdown()` - Get status distribution for today

### DOM Update Functions
- `updateSummaryCards()` - Update header card numbers
- `updateStatusBoxes()` - Update status overview
- `updateHeaderPickupCount()` - Update header badge
- `populateTodaysPickupsTable()` - Populate pickup table
- `populatePendingPickupsTable()` - Populate detailed pickup table
- `populateTodaysOrdersTable()` - Populate detailed orders table
- `populateTomorrowsSchedule()` - Populate schedule preview

### Chart Functions
- `initTodaysStatusChart()` - Initialize pie chart
- `initTopProductsChart()` - Initialize horizontal bar chart
- `initQuarterlyRevenueChart()` - Initialize quarterly bar chart
- `initializeCharts()` - Initialize all charts

## 🎨 Design Features

### Color Scheme
- **Primary**: #C44569 (Raspberry)
- **Background**: #FAF5F0 (Cream)
- **Text**: #2B2B2B (Dark)
- **Success**: #10B981 (Green)
- **Amber**: #F59E0B (Orange)
- **Purple**: #A855F7 (Purple)
- **Gray**: #6B7280 (Neutral)

### Layout
- **Fixed Header** (70px) with manager info and quick stats
- **Fixed Sidebar** (220px) with navigation
- **Responsive Main Content** that scrolls independently
- **Mobile-Friendly**: Adapts to smaller screens

### Components
- Summary cards with hover effects
- Status badges with color coding
- Interactive data tables with search/filter
- Compact, easy-to-read charts
- Schedule preview items
- Action buttons with clear hierarchy

## 📱 Responsive Design

The dashboard is fully responsive:
- **Desktop (1200px+)**: Full layout with all features
- **Tablet (768px-1200px)**: Adjusted grid layouts
- **Mobile (480px-768px)**: Stacked layout, condensed tables
- **Small Mobile (<480px)**: Single column, minimal padding

## 📝 Sample Data

The dashboard comes with sample data including:
- 6 orders for today (various statuses)
- 1 order from yesterday
- 5 orders from earlier in the week (for revenue calculations)
- 12 customer profiles
- 4 items in tomorrow's schedule

All dates are calculated relative to today, so data is always current.

## 🔐 Authentication

The dashboard assumes the user is already logged in as:
- **Role**: Manager
- **Name**: Emily Boudreaux

To change manager info, edit the header in each HTML file (line ~17):
```html
<div class="manager-name">Your Name Here</div>
```

## 🚀 Customization

### Add New Data
Edit `js/main.js` and add to the `dashboardData` object:
```javascript
dashboardData.orders.push({
    orderId: 'ORD-013',
    customerName: 'New Customer',
    phone: '(555) 123-4567',
    // ... other fields
});
```

### Change Colors
Edit `:root` variables in `css/styles.css`:
```css
:root {
    --primary: #C44569;
    --background: #FAF5F0;
    /* ... more colors */
}
```

### Add New Pages
1. Create new HTML file with same header/sidebar structure
2. Add nav link to sidebar in all pages
3. Add initialization function in `js/main.js` if data is needed
4. Update `initializeNav()` to mark active page

## 📦 Dependencies

- **Chart.js** (v3.9.1) - For charts (loaded from CDN)
- No other dependencies!

## 🧪 Testing

All features work in modern browsers:
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers

### Test the Features
1. **Dashboard**: View all cards, charts, and tables
2. **Summary Cards**: Click "View Details" to navigate
3. **Search**: Try searching in pending pickups or today's orders
4. **Filters**: Test status and availability filters
5. **Mobile**: Resize browser window to test responsiveness
6. **Charts**: Hover over charts to see interactive tooltips

## 📄 License

This is a college student project for Emily Bakes Cakes bakery management.

## 💡 Notes

- All data is stored in memory (refresh page to reset)
- For persistent data, you would need a backend database
- Charts update dynamically based on data in `dashboardData`
- Tables have 6-8 sample rows but can display more
- All calculations are done in real-time JavaScript

---

**Version**: 1.0  
**Last Updated**: November 2025
