# Data Structure Reference

This document explains the complete data model used in the Emily Bakes Cakes Manager Dashboard.

## Data Location

All data is stored in `js/main.js` in the global `dashboardData` object.

## Order Schema

Each order in `dashboardData.orders` has the following structure:

```javascript
{
    orderId: 'ORD-001',                          // Unique order identifier
    customerName: 'Sarah Mitchell',              // Full customer name
    phone: '(555) 123-4567',                     // Customer phone number
    orderTime: new Date(...),                    // When order was placed
    pickupDate: getTodayStart(),                 // Date of pickup
    pickupTime: new Date(...),                   // Time of pickup
    cakeType: 'Chocolate Velvet',                // Cake flavor/type
    layers: 3,                                   // Number of cake layers (2-4)
    total: 65.00,                                // Order total in dollars
    status: 'Ready'                              // Current order status
}
```

### Order Status Options

| Status | Meaning |
|--------|---------|
| `To Be Created` | Order just placed, not yet started |
| `In Baking` | Cake is currently baking |
| `Decorating` | Cake is being decorated |
| `Ready` | Cake is ready for customer pickup |
| `Picked Up` | Customer has picked up the order |

### Cake Type Options (Examples)

- Chocolate Velvet
- Vanilla Dream
- Red Velvet
- Strawberry Bliss
- Lemon Zest
- Carrot Cake

(You can add more types as needed)

## Customer Schema

Each customer in `dashboardData.customers` has the following structure:

```javascript
{
    id: 'CUST-001',                              // Unique customer identifier
    name: 'Sarah Mitchell',                      // Full customer name
    phone: '(555) 123-4567',                     // Phone number
    email: 'sarah.mitchell@email.com',           // Email address
    orders: ['ORD-001'],                         // Array of order IDs
    createdDate: new Date(...)                   // Account creation date
}
```

### Customer Registration

- `createdDate` determines if customer is "new this week"
- A customer is new if created within the last 7 days
- Can have multiple orders (orders array)

## Tomorrow's Schedule Schema

Each item in `dashboardData.tomorrowSchedule` has the following structure:

```javascript
{
    time: '10:00 AM',                            // Pickup/delivery time
    customer: 'Angela Price',                    // Customer name
    summary: 'Chocolate Cake - 3 layers'         // Brief order summary
}
```

## Computed Functions

The system provides functions to calculate metrics from the raw data:

### Date Functions

```javascript
getTodayStart()        // Returns today at midnight
getWeekAgo()          // Returns date 7 days ago at midnight
getTodayFormatted()   // Returns formatted string (e.g., "Friday, November 21, 2025")
formatTime(date)      // Returns time string (e.g., "3:45 PM")
formatDate(date)      // Returns date string (e.g., "Nov 21, 2025")
formatDateTime(date)  // Returns full string (e.g., "Nov 21, 2025 at 3:45 PM")
formatCurrency(amount) // Returns currency string (e.g., "$65.00")
```

### Query Functions

```javascript
getTodaysOrders()
// Returns array of all orders where pickupDate = today

getPendingPickups()
// Returns array of orders where status = 'Ready' and pickupDate = today

getPendingPickupCount()
// Returns number: count of pending pickups

getTodaysOrderCount()
// Returns number: count of all today's orders

getNewCustomersThisWeek()
// Returns array of customers created in last 7 days

getNewCustomersCount()
// Returns number: count of new customers this week

getWeeklyRevenue()
// Returns number: sum of all completed orders (Picked Up) in last 7 days

getStatusCounts()
// Returns object with counts for each status:
// {
//     toBaking: number,
//     baking: number,
//     decorating: number,
//     ready: number,
//     pickedUp: number
// }

getTopProductsThisWeek()
// Returns array of top 5 cake types ordered this week:
// [
//     { name: 'Chocolate Velvet', count: 3 },
//     { name: 'Vanilla Dream', count: 2 },
//     ...
// ]

getTodaysStatusBreakdown()
// Returns array with count for each status today:
// [
//     { status: 'To Be Created', count: 1 },
//     { status: 'In Baking', count: 1 },
//     ...
// ]

getQuarterlyRevenue()
// Returns object with quarterly revenue:
// {
//     'Q1': 1250.00,
//     'Q2': 1450.00,
//     'Q3': 1600.00,
//     'Q4': 1300.00
// }
```

## Sample Data Breakdown

### Orders (12 total)
- **6 Today**:
  - 1 Ready (Sarah Mitchell)
  - 1 Decorating (John Reyes)
  - 1 In Baking (Emma Wilson)
  - 1 Ready (Michael Chen)
  - 1 To Be Created (Lisa Thompson)
  - 1 Decorating (David Martinez)
- **1 Yesterday**: Picked Up
- **5 Last 7 Days**: All Picked Up (for revenue calculation)

### Customers (12 total)
- **6 New This Week**: John Reyes, Emma Wilson, Lisa Thompson, David Martinez, plus 2 others
- **6 Existing**: Various creation dates

### Schedule
- **Tomorrow**: 4 scheduled pickups/deliveries

## Working with Data

### To Add a New Order

```javascript
dashboardData.orders.push({
    orderId: 'ORD-999',
    customerName: 'New Customer Name',
    phone: '(555) 123-4567',
    orderTime: new Date(), // Order placed now
    pickupDate: getTodayStart(), // For today
    pickupTime: new Date(getTodayStart().getTime() + 16 * 60 * 60 * 1000), // 4 PM
    cakeType: 'Chocolate Cake',
    layers: 2,
    total: 50.00,
    status: 'To Be Created'
});
```

### To Add a New Customer

```javascript
dashboardData.customers.push({
    id: 'CUST-999',
    name: 'New Customer Name',
    phone: '(555) 123-4567',
    email: 'email@example.com',
    orders: ['ORD-999'], // Reference new order
    createdDate: new Date() // Today
});
```

### To Add Tomorrow's Schedule

```javascript
dashboardData.tomorrowSchedule.push({
    time: '11:00 AM',
    customer: 'Jane Doe',
    summary: 'Vanilla Cake - 2 layers'
});
```

## Updating Existing Data

### Change Order Status

```javascript
dashboardData.orders.find(o => o.orderId === 'ORD-001').status = 'Ready';
```

### Update Customer Email

```javascript
dashboardData.customers.find(c => c.id === 'CUST-001').email = 'newemail@example.com';
```

### Refresh Dashboard

After modifying data, refresh the page to update all displays:

```javascript
// In browser console:
location.reload();

// Or call initialization again:
initializeDashboard(); // Updates dashboard
initializePendingPickups(); // Updates pending pickups page
initializeTodaysOrders(); // Updates today's orders page
```

## Data Notes

- **No Persistence**: Data is stored in memory. Refreshing the page resets everything.
- **For Persistence**: You would need to add a backend (Node.js, Python, etc.) with a database.
- **Real-Time Calculations**: All metrics are calculated from the data on every page load.
- **Date Calculations**: Dates are relative to `getTodayStart()` so data is always current.

## Chart Data Sources

### Today's Status Pie Chart
```javascript
getTodaysStatusBreakdown()
// Breakdown of today's orders by status
```

### Top Products Bar Chart
```javascript
getTopProductsThisWeek()
// Top 5 cake types ordered in last 7 days
```

### Quarterly Revenue Chart
```javascript
getQuarterlyRevenue()
// Revenue for Q1, Q2, Q3, Q4
```

## Table Data Sources

### Today's Pickups Table
```javascript
getTodaysOrders()
// Sorted by pickup time
// Limited to 6 rows for dashboard view
```

### Pending Pickups Table
```javascript
getTodaysOrders()
// Filtered by status
// Searchable by Order ID, Customer, Phone
```

### Today's Orders Table
```javascript
getTodaysOrders()
// Filtered by status
// Searchable by Order ID, Customer, Cake Type
```

---

**For questions**: Review the functions in `js/main.js` or check README.md for more information.
