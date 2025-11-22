# JavaScript API Reference

Complete reference for all functions in `js/main.js`

## Table of Contents

1. [Helper Functions](#helper-functions)
2. [Query Functions](#query-functions)
3. [Calculation Functions](#calculation-functions)
4. [DOM Update Functions](#dom-update-functions)
5. [Chart Functions](#chart-functions)
6. [Page Initialization](#page-initialization)
7. [Utility Functions](#utility-functions)

---

## Helper Functions

### Date/Time Functions

#### `getTodayStart()`
Returns a Date object for today at midnight (00:00:00).

```javascript
const today = getTodayStart();
// Returns: 2025-11-21T00:00:00.000Z (at midnight)
```

#### `getWeekAgo()`
Returns a Date object for 7 days ago at midnight.

```javascript
const weekAgo = getWeekAgo();
// Returns: 2025-11-14T00:00:00.000Z
```

#### `getTodayFormatted()`
Returns today's date as a formatted string.

```javascript
const dateStr = getTodayFormatted();
// Returns: "Friday, November 21, 2025"
```

#### `formatTime(date)`
Converts a Date to time format (HH:MM AM/PM).

**Parameters:**
- `date` (Date): The date to format

**Returns:** String (e.g., "03:45 PM")

```javascript
const time = formatTime(new Date());
// Returns: "03:45 PM"
```

#### `formatDate(date)`
Converts a Date to date format (Mon DD, YYYY).

**Parameters:**
- `date` (Date): The date to format

**Returns:** String (e.g., "Nov 21, 2025")

```javascript
const date = formatDate(new Date());
// Returns: "Nov 21, 2025"
```

#### `formatDateTime(date)`
Converts a Date to full format (Mon DD, YYYY at HH:MM AM/PM).

**Parameters:**
- `date` (Date): The date to format

**Returns:** String (e.g., "Nov 21, 2025 at 03:45 PM")

```javascript
const datetime = formatDateTime(new Date());
// Returns: "Nov 21, 2025 at 03:45 PM"
```

#### `formatCurrency(amount)`
Converts a number to currency format.

**Parameters:**
- `amount` (Number): The amount to format

**Returns:** String (e.g., "$65.00")

```javascript
const price = formatCurrency(65);
// Returns: "$65.00"
```

---

## Query Functions

These functions search and filter the data.

#### `getTodaysOrders()`
Returns all orders where the pickup date is today.

**Returns:** Array of order objects

```javascript
const orders = getTodaysOrders();
// Returns: [
//   { orderId: 'ORD-001', customerName: 'Sarah', ... },
//   { orderId: 'ORD-002', customerName: 'John', ... },
//   ...
// ]
```

#### `getPendingPickups()`
Returns all orders with status "Ready" for today.

**Returns:** Array of order objects (subset of today's orders)

```javascript
const pickups = getPendingPickups();
// Returns: [
//   { orderId: 'ORD-001', status: 'Ready', ... },
//   { orderId: 'ORD-004', status: 'Ready', ... }
// ]
```

#### `getNewCustomersThisWeek()`
Returns all customers created within the last 7 days.

**Returns:** Array of customer objects

```javascript
const newCustomers = getNewCustomersThisWeek();
// Returns: [
//   { id: 'CUST-002', name: 'John Reyes', createdDate: ..., ... },
//   { id: 'CUST-003', name: 'Emma Wilson', createdDate: ..., ... },
//   ...
// ]
```

---

## Calculation Functions

These functions compute metrics from the data.

#### `getPendingPickupCount()`
Returns the number of orders ready for pickup today.

**Returns:** Number (integer)

```javascript
const count = getPendingPickupCount();
// Returns: 2
```

#### `getTodaysOrderCount()`
Returns the total number of orders placed today.

**Returns:** Number (integer)

```javascript
const count = getTodaysOrderCount();
// Returns: 6
```

#### `getNewCustomersCount()`
Returns the number of new customers this week.

**Returns:** Number (integer)

```javascript
const count = getNewCustomersCount();
// Returns: 4
```

#### `getWeeklyRevenue()`
Returns the sum of all completed orders (Picked Up) in the last 7 days.

**Returns:** Number (currency, e.g., 450.50)

```javascript
const revenue = getWeeklyRevenue();
// Returns: 450.50
// Display with: formatCurrency(revenue) → "$450.50"
```

#### `getStatusCounts()`
Returns counts of orders by status for today.

**Returns:** Object with status counts

```javascript
const counts = getStatusCounts();
// Returns: {
//   toBaking: 1,
//   baking: 1,
//   decorating: 2,
//   ready: 2,
//   pickedUp: 0
// }
```

#### `getTopProductsThisWeek()`
Returns the top 5 most-ordered cake types this week.

**Returns:** Array of objects with name and count

```javascript
const topProducts = getTopProductsThisWeek();
// Returns: [
//   { name: 'Chocolate Velvet', count: 3 },
//   { name: 'Vanilla Dream', count: 2 },
//   { name: 'Red Velvet', count: 2 },
//   ...
// ]
```

#### `getTodaysStatusBreakdown()`
Returns the distribution of all statuses for today's orders.

**Returns:** Array of objects with status and count

```javascript
const breakdown = getTodaysStatusBreakdown();
// Returns: [
//   { status: 'To Be Created', count: 1 },
//   { status: 'In Baking', count: 1 },
//   { status: 'Decorating', count: 2 },
//   { status: 'Ready', count: 2 },
//   { status: 'Picked Up', count: 0 }
// ]
```

#### `getQuarterlyRevenue()`
Returns revenue for Q1, Q2, Q3, and Q4.

**Returns:** Object with quarterly totals

```javascript
const quarterly = getQuarterlyRevenue();
// Returns: {
//   'Q1': 1250.00,
//   'Q2': 1450.00,
//   'Q3': 1600.00,
//   'Q4': 1300.00
// }
```

---

## DOM Update Functions

These functions update HTML elements with data.

#### `updateSummaryCards()`
Updates all 4 summary card numbers on the dashboard.

**Updates:**
- `#pending-pickup-count` - Pending pickups
- `#todays-orders-count` - Today's order count
- `#weekly-revenue` - Formatted currency
- `#new-customers-count` - New customers this week

```javascript
updateSummaryCards();
// Updates: card numbers to match current data
```

#### `updateStatusBoxes()`
Updates the 3 status overview boxes.

**Updates:**
- `#status-baking` - Pending baking (To Be Created + In Baking)
- `#status-decorating` - Pending decorating
- `#status-ready` - Ready for pickup

```javascript
updateStatusBoxes();
// Updates: status box numbers
```

#### `updateHeaderPickupCount()`
Updates the header badge with pickup count.

**Updates:**
- `#header-pickup-count` - Displays "X pickups today"

```javascript
updateHeaderPickupCount();
// Updates: header badge (e.g., "2 pickups today")
```

#### `populateTodaysPickupsTable()`
Populates the dashboard's today's pickups table.

**Updates:**
- `#todays-pickups-table tbody` - Table rows

```javascript
populateTodaysPickupsTable();
// Populates: 6 rows of today's pickups (sorted by time)
```

#### `populatePendingPickupsTable(searchTerm, filterStatus)`
Populates the pending pickups page table with search/filter.

**Parameters:**
- `searchTerm` (String): Search text (optional)
- `filterStatus` (String): Filter status - "All", "Ready", "Not Ready" (optional)

**Updates:**
- `#pending-pickups-table tbody` - Filtered table rows
- `#results-count` - Result count

```javascript
populatePendingPickupsTable('Mitchell', 'Ready');
// Populates: table filtered by customer name and ready status
// Updates: results count (e.g., "1 result")

// Called by:
document.getElementById('search-input').addEventListener('input', (e) => {
    populatePendingPickupsTable(e.target.value, filterStatus);
});
```

#### `populateTodaysOrdersTable(searchTerm, filterStatus)`
Populates the today's orders page table with search/filter.

**Parameters:**
- `searchTerm` (String): Search text (optional)
- `filterStatus` (String): Filter status - "All", "To Be Created", "In Baking", "Decorating", "Ready", "Picked Up" (optional)

**Updates:**
- `#todays-orders-table tbody` - Filtered table rows
- `#results-count` - Result count

```javascript
populateTodaysOrdersTable('Chocolate', 'Ready');
// Populates: table filtered by cake type and ready status

// Called by:
document.getElementById('search-input').addEventListener('input', (e) => {
    populateTodaysOrdersTable(e.target.value, filterStatus);
});
```

#### `populateTomorrowsSchedule()`
Populates the tomorrow's schedule preview section.

**Updates:**
- `#tomorrows-schedule` - Schedule items

```javascript
populateTomorrowsSchedule();
// Populates: 4 schedule items with time, customer, summary
```

#### `viewOrderDetails(orderId)`
Placeholder function for viewing order details.

**Parameters:**
- `orderId` (String): The order ID to view

```javascript
viewOrderDetails('ORD-001');
// Currently shows alert, can be enhanced to show modal
```

---

## Chart Functions

These functions create and manage Chart.js charts.

#### `initTodaysStatusChart()`
Initializes the today's order status pie chart.

**Updates:**
- `#todaysStatusChart` - Pie chart canvas

**Chart Type:** Doughnut (pie)

**Data Source:** `getTodaysStatusBreakdown()`

```javascript
initTodaysStatusChart();
// Creates: pie chart of today's order statuses
```

#### `initTopProductsChart()`
Initializes the top products horizontal bar chart.

**Updates:**
- `#topProductsChart` - Bar chart canvas

**Chart Type:** Horizontal bar

**Data Source:** `getTopProductsThisWeek()`

```javascript
initTopProductsChart();
// Creates: horizontal bar chart of top 5 products
```

#### `initQuarterlyRevenueChart()`
Initializes the quarterly revenue bar chart.

**Updates:**
- `#quarterlyRevenueChart` - Bar chart canvas

**Chart Type:** Vertical bar

**Data Source:** `getQuarterlyRevenue()`

```javascript
initQuarterlyRevenueChart();
// Creates: bar chart comparing Q1-Q4 revenue
```

#### `initializeCharts()`
Initializes all three charts (calls the above functions).

```javascript
initializeCharts();
// Creates: all three charts
// Call this once when the dashboard loads
```

---

## Page Initialization

These functions set up pages when they load.

#### `initializeDashboard()`
Initializes the main dashboard page.

**Calls:**
- `updateSummaryCards()`
- `updateStatusBoxes()`
- `updateHeaderPickupCount()`
- `populateTodaysPickupsTable()`
- `populateTomorrowsSchedule()`
- `initializeCharts()`

```javascript
initializeDashboard();
// Called automatically on index.html load
```

#### `initializePendingPickups()`
Initializes the pending pickups page.

**Calls:**
- Updates page date
- `populatePendingPickupsTable()`
- Sets up search and filter listeners

```javascript
initializePendingPickups();
// Called automatically on pending_pickups.html load
```

#### `initializeTodaysOrders()`
Initializes the today's orders page.

**Calls:**
- Updates page date
- `populateTodaysOrdersTable()`
- Sets up search and filter listeners

```javascript
initializeTodaysOrders();
// Called automatically on todays_orders.html load
```

#### `initializeNav()`
Sets the active navigation link based on current page.

```javascript
initializeNav();
// Highlights the current page in the sidebar
```

---

## Utility Functions

#### `handleLogout()`
Logs out the user (shows alert and redirects).

```javascript
handleLogout();
// Shows: "Logging out..." alert
// Redirects: to ../index.html
```

#### `backToSite()`
Navigates back to the main website.

```javascript
backToSite();
// Redirects: to ../index.html
```

---

## Data Model

### Global Data Object

```javascript
dashboardData = {
    orders: [
        {
            orderId: 'ORD-001',
            customerName: 'Sarah Mitchell',
            phone: '(555) 123-4567',
            orderTime: Date,
            pickupDate: Date,
            pickupTime: Date,
            cakeType: 'Chocolate Velvet',
            layers: 3,
            total: 65.00,
            status: 'Ready'
        },
        // ... more orders
    ],
    customers: [
        {
            id: 'CUST-001',
            name: 'Sarah Mitchell',
            phone: '(555) 123-4567',
            email: 'sarah@email.com',
            orders: ['ORD-001'],
            createdDate: Date
        },
        // ... more customers
    ],
    tomorrowSchedule: [
        {
            time: '10:00 AM',
            customer: 'Angela Price',
            summary: 'Chocolate Cake - 3 layers'
        },
        // ... more schedule items
    ]
}
```

---

## Common Usage Patterns

### Update Dashboard After Adding Order

```javascript
// 1. Add new order to data
dashboardData.orders.push({
    orderId: 'ORD-999',
    customerName: 'New Customer',
    phone: '(555) 123-4567',
    orderTime: new Date(),
    pickupDate: getTodayStart(),
    pickupTime: new Date(getTodayStart().getTime() + 16 * 60 * 60 * 1000),
    cakeType: 'Chocolate Cake',
    layers: 2,
    total: 50.00,
    status: 'To Be Created'
});

// 2. Update dashboard
updateSummaryCards();
updateStatusBoxes();
updateHeaderPickupCount();
populateTodaysPickupsTable();
initializeCharts();
```

### Filter Table Dynamically

```javascript
// User types in search box
const searchTerm = 'Mitchell';
const filterStatus = 'Ready';

// Update table with search and filter
populatePendingPickupsTable(searchTerm, filterStatus);
// Shows only "Ready" pickups from "Mitchell"
```

### Get Specific Metric

```javascript
// Get pending pickup count
const count = getPendingPickupCount();
console.log(`${count} pickups ready`);

// Get weekly revenue
const revenue = getWeeklyRevenue();
console.log(`This week: ${formatCurrency(revenue)}`);

// Get new customers
const newCustomers = getNewCustomersThisWeek();
console.log(`${newCustomers.length} new customers this week`);
```

### Format Data for Display

```javascript
// Format a date
const date = new Date();
console.log(formatDate(date));        // "Nov 21, 2025"
console.log(formatTime(date));        // "03:45 PM"
console.log(formatDateTime(date));    // "Nov 21, 2025 at 03:45 PM"

// Format a price
const price = 65.5;
console.log(formatCurrency(price));   // "$65.50"
```

---

## Event Listeners (Set Up in Init Functions)

### Search Input
```javascript
document.getElementById('search-input').addEventListener('input', (e) => {
    const filterVal = filterDropdown ? filterDropdown.value : 'All';
    populatePendingPickupsTable(e.target.value, filterVal);
});
```

### Filter Dropdown
```javascript
document.getElementById('filter-dropdown').addEventListener('change', (e) => {
    const searchVal = searchInput ? searchInput.value : '';
    populatePendingPickupsTable(searchVal, e.target.value);
});
```

---

## Error Handling

Most functions have built-in null checks:

```javascript
// Safe to call even if element doesn't exist
const el = document.getElementById('nonexistent');
if (el) el.textContent = 'Text'; // Won't error

// Functions check if elements exist
const tbody = document.querySelector('#pending-pickups-table tbody');
if (!tbody) return; // Exit early if not found
```

---

## Performance Notes

- All functions run synchronously (instantly)
- No async/await or promises
- No API calls or network requests
- All data is in memory
- Search and filter are instant (<50ms)
- Charts render in <500ms

---

## Further Customization

### Add a New Computed Function

```javascript
function getAverageCakePrice() {
    const orders = dashboardData.orders;
    const totalPrice = orders.reduce((sum, o) => sum + o.total, 0);
    return totalPrice / orders.length;
}

// Use it:
const avg = getAverageCakePrice();
console.log('Average order: ' + formatCurrency(avg));
```

### Add a New Status

1. Add to order status in data
2. Add case in `getStatusCounts()`
3. Add styling in CSS (`.status-new-status`)
4. Update filter dropdowns in HTML

---

**For full documentation, see README.md and DATA_STRUCTURE.md**
