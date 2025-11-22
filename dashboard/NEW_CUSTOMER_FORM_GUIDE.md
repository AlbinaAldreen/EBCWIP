# New Customer Form Guide

## Overview
A comprehensive customer registration form has been created and integrated throughout the staff-facing dashboard application. The form captures all customer data according to the database schema provided.

## File Location
- **Form File**: `dashboard/new-customer.html`
- **Direct URL**: `http://localhost:8000/dashboard/new-customer.html`

## Form Sections

### 1. Personal Information
- **First Name** (Required) - Max 25 characters
- **Middle Initial** (Optional) - Single character
- **Last Name** (Required) - Max 50 characters
- **Company Name** (Optional) - Max 60 characters
- **Customer Type** (Required) - Dropdown: Retail (Individual) or Corporate (Business)
- **Customer Status** (Required) - Dropdown: Active, Inactive, Prospect, Do Not Contact

### 2. Address Information
- **Address Line 1** (Required) - Max 60 characters
- **Address Line 2** (Optional) - Max 60 characters
- **State / Province** (Required) - Dropdown with US states
- **Zip Code** (Required) - Max 10 characters
- **Country** (Required) - Dropdown: USA, Canada, Mexico

### 3. Contact Information
- **Mobile Phone** (Required) - Format: (999) 999-9999
- **Work Phone** (Optional) - Format: (999) 999-9999
- **Home Phone** (Optional) - Format: (999) 999-9999
- **Email Address** (Required) - Valid email format

### 4. Additional Information
- **Comments About Customer** (Optional) - Max 1000 characters for notes
- **Preferred Customer** (Optional) - Checkbox to mark as preferred (eligible for discounts)

## Data Validation
- Required fields are marked with a red asterisk (*)
- Email validation ensures valid email format
- Phone number validation checks for proper format
- Duplicate email prevention (checks against existing customers)
- All text fields have maximum character limits matching the database schema

## Features
✅ **Professional UI Design**
- Matches the premium dashboard redesign aesthetic
- Responsive layout for desktop, tablet, and mobile
- Clear section organization with icons
- Helpful text hints for each field

✅ **Data Persistence**
- Customer data stored in browser's localStorage
- Automatic customer ID generation
- Success/error message feedback
- Auto-redirect to all-customers.html upon successful creation

✅ **User Experience**
- Submit, Clear, and Cancel buttons
- Confirmation dialog before cancellation
- Real-time field validation
- Success notification with auto-redirect (2 seconds)

## Navigation Integration

The "New Customer" form is linked from all staff-facing pages:

### Dashboard Pages
- ✅ manager-dashboard.html
- ✅ sales-dashboard.html
- ✅ baker-dashboard.html
- ✅ decorator-dashboard.html

### Staff Pages
- ✅ index.html (Main Dashboard)
- ✅ all-customers.html (Dual buttons: "Comprehensive Form" and "Quick Add")
- ✅ all-orders.html
- ✅ orders.html
- ✅ customers.html
- ✅ reports.html
- ✅ settings.html
- ✅ todays_orders.html
- ✅ pending_pickups.html

## Access Methods

### Method 1: Direct Link
Navigate directly to `http://localhost:8000/dashboard/new-customer.html`

### Method 2: From Any Dashboard
Click "➕ New Customer" in the sidebar navigation (visible on all staff pages)

### Method 3: From All Customers Page
Click "Comprehensive Form" button at the top of the customer list

## Form Submit Flow
1. User fills out form with customer information
2. Form validation checks all required fields and formats
3. On success:
   - Customer data saved to localStorage
   - Green success message displayed
   - Auto-redirect to all-customers.html (2 seconds)
4. On error:
   - Red error message displayed with description
   - User can correct and resubmit

## Database Schema Mapping

| Form Field | Database Field | Type | Required | Max Length |
|---|---|---|---|---|
| First Name | Cust_First_Name | Varchar | Yes | 25 |
| Middle Initial | Cust_Middle_Init | Char | No | 1 |
| Last Name | Cust_Last_Name | Varchar | Yes | 50 |
| Company Name | Company Name | Varchar | No | 60 |
| Customer Type | Cust_Type_Id | Integer | Yes | 2 |
| Customer Status | Cust_Status_Id | Integer | Yes | 2 |
| Address Line 1 | Cust_Addr_Line1 | Varchar | Yes | 60 |
| Address Line 2 | Cust_Addr_Line2 | Varchar | No | 60 |
| State | State_Id | Integer | Yes | 2 |
| Zip Code | CustZipCode | Char | Yes | 10 |
| Country | Country_Id | Integer | Yes | 3 |
| Mobile Phone | Cust_Mobile_Phone | Char | Yes | 20 |
| Work Phone | Work_Phone | Char | No | 20 |
| Home Phone | Cust_Home_Phone | Char | No | 20 |
| Email | Cust_Email_Addr | Varchar | Yes | 40 |
| Comments | Comments about Customer | Varchar | No | 1000 |
| Preferred Customer | Preferred Customer | Char | No | 1 |

## Technical Details

### HTML Structure
- Semantic HTML5 form elements
- Organized with fieldsets (form-section divs)
- Proper label associations (for/id attributes)
- Accessible error/success messaging

### CSS Styling
- Responsive grid layout (auto-fit, minmax(300px, 1fr))
- Mobile-first approach with media queries
- Consistent color scheme matching dashboard redesign
- Focus states for accessibility
- Hover effects for better UX

### JavaScript Functionality
- Form validation on submit
- localStorage integration for data persistence
- User session tracking (role and name)
- Error/success notification system
- Navigation helpers (back, logout)

## Future Enhancements

Potential improvements for backend integration:
1. Replace localStorage with API calls to backend
2. Implement real customer ID generation from database
3. Add async email validation against existing records
4. Integrate with customer relationship management (CRM)
5. Add file upload for customer profile photos
6. Implement customer approval workflow
7. Add audit logging for customer creation
8. Create customer groups/segments
9. Add import/export functionality
10. Implement customer duplicate detection

## Support
For questions or modifications to the form structure, contact the development team.
The form is fully self-contained and can be easily customized to add new fields or modify existing ones.
