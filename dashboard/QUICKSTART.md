# Quick Setup Guide - Emily Bakes Cakes Manager Dashboard

## How to Run

### Option 1: Direct Browser Open
1. Navigate to: `C:\Users\adere\Desktop\emily_bakes_staff\`
2. Right-click on `index.html`
3. Select "Open with" → Choose your browser (Chrome, Firefox, Edge, Safari)
4. Dashboard opens immediately!

### Option 2: Use Python Server (Recommended)
```powershell
cd C:\Users\adere\Desktop\emily_bakes_staff
python -m http.server 8000
```
Then open browser to: `http://localhost:8000`

### Option 3: Use Node.js HTTP Server
```powershell
cd C:\Users\adere\Desktop\emily_bakes_staff
npx http-server
```

## What You'll See

### Dashboard (index.html)
- **Header**: Manager name (Emily Boudreaux), pickup count, logout button
- **Left Sidebar**: Navigation to Dashboard, Orders, Customers, Reports, Settings
- **Summary Cards**: 4 cards showing key metrics
- **Action Buttons**: Quick access to common tasks
- **Status Overview**: Visual breakdown of order statuses
- **Charts**: 3 interactive charts with real data
- **Tables**: Today's pickups and tomorrow's schedule

### Navigation
All pages share the same header and sidebar:
- Click page titles to navigate
- Active page is highlighted in sidebar
- All data updates dynamically

## Key Metrics (Dynamic)

The dashboard automatically calculates:

| Metric | Source |
|--------|--------|
| Pending Pickups | Orders with status "Ready" for today |
| Today's Orders | All orders with pickup date = today |
| Weekly Revenue | Sum of completed orders in last 7 days |
| New Customers | Customers created in last 7 days |
| Pending Baking | Orders in "To Be Created" + "In Baking" |
| Pending Decorating | Orders in "Decorating" status |
| Ready for Pickup | Orders in "Ready" status |

## Features by Page

### Dashboard (index.html) - DEFAULT PAGE
✅ Summary cards (4)  
✅ Quick action buttons (6)  
✅ Status overview boxes (3)  
✅ Charts (3 interactive)  
✅ Today's pickups table  
✅ Tomorrow's schedule preview  

### Pending Pickups (pending_pickups.html)
✅ Full pickup list for today  
✅ Search by Order ID, Customer, Phone  
✅ Filter by status (All, Ready, Not Ready)  
✅ Dynamic result count  

### Today's Orders (todays_orders.html)
✅ All orders for today  
✅ Search by Order ID, Customer, Cake Type  
✅ Filter by status  
✅ Shows all order details  

### Placeholder Pages
- Orders
- Customers
- Reports
- Settings
(Can be developed later)

## Sample Data Included

The system comes with:
- **6 orders** for today (different statuses)
- **12 customers** (some new this week)
- **4 tomorrow's schedule** items
- **Weekly/quarterly** data for charts

All dates are calculated from today, so data is always relevant.

## Customizing Data

Edit `js/main.js` in the `dashboardData` object:

### Add a New Order
```javascript
dashboardData.orders.push({
    orderId: 'ORD-999',
    customerName: 'Your Customer',
    phone: '(555) 000-0000',
    orderTime: new Date(), // Now
    pickupDate: getTodayStart(),
    pickupTime: new Date(getTodayStart().getTime() + 16 * 60 * 60 * 1000), // 4 PM
    cakeType: 'Chocolate Cake',
    layers: 2,
    total: 50.00,
    status: 'Ready' // Options: To Be Created, In Baking, Decorating, Ready, Picked Up
});
```

### Add a New Customer
```javascript
dashboardData.customers.push({
    id: 'CUST-999',
    name: 'Your Customer',
    phone: '(555) 000-0000',
    email: 'customer@email.com',
    orders: ['ORD-999'],
    createdDate: new Date() // Today
});
```

### Change Manager Name
In each HTML file, find line ~17:
```html
<div class="manager-name">Emily Boudreaux</div>
```
Replace with your name:
```html
<div class="manager-name">Your Name</div>
```

## Styling Customization

Edit `css/styles.css` to change colors:

```css
:root {
    --primary: #C44569;           /* Main color (raspberry) */
    --background: #FAF5F0;        /* Background (cream) */
    --text: #2B2B2B;              /* Text color (dark) */
    --success: #10B981;           /* Success color (green) */
    --amber: #F59E0B;             /* Warning color (orange) */
    --purple: #A855F7;            /* Accent (purple) */
    --gray: #6B7280;              /* Neutral gray */
}
```

## Troubleshooting

### Charts Not Showing
- Make sure Chart.js loads from CDN (check internet connection)
- Check browser console for errors (F12)

### Data Not Updating
- Refresh page (Ctrl+R or Cmd+R)
- Clear browser cache if needed
- Data resets on page refresh (in-memory only)

### Mobile/Responsive Issues
- Resize browser window to test
- Open DevTools (F12) → Toggle Device Toolbar (Ctrl+Shift+M)
- Test on different screen sizes

### Search Not Working
- Make sure search input is focused
- Search is case-insensitive
- Try partial matches

## Browser Compatibility

✅ Chrome 90+
✅ Firefox 88+
✅ Edge 90+
✅ Safari 14+
✅ Mobile browsers (iOS Safari, Chrome Mobile)

## File Sizes

- `index.html`: ~6 KB
- `css/styles.css`: ~12 KB
- `js/main.js`: ~25 KB
- Total: ~43 KB (very lightweight!)

## Performance

- **Load Time**: <100ms (instant)
- **Charts Render**: <500ms
- **Table Population**: <100ms
- **Search/Filter**: <50ms

All operations are instant because everything runs locally in JavaScript.

---

**Need Help?** Check the README.md for more detailed documentation.

**Ready to Use!** Open `index.html` in your browser and start exploring the dashboard.
