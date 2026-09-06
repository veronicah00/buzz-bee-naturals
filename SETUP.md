# Setup Guide - Buzz Bee Naturals Website

## Quick Start (Recommended)

### Windows Users

**Option 1: Using Batch File (Easiest)**
1. Double-click `start.bat`
2. Wait for dependencies to install
3. Browser will open to `http://localhost:5000`

**Option 2: Using PowerShell**
1. Right-click `start.ps1`
2. Select "Run with PowerShell"
3. Allow execution if prompted
4. Browser will open to `http://localhost:5000`

**Option 3: Manual Setup**
```powershell
# Open PowerShell in the project folder
pip install -r requirements.txt
python app.py
```

---

## Detailed Setup Steps

### Step 1: Install Python

1. Download Python 3.9+ from https://www.python.org/
2. During installation:
   - ✓ Check "Add Python to PATH"
   - ✓ Check "Install pip"
3. Click Install
4. Verify installation:
   ```cmd
   python --version
   ```

### Step 2: Prepare Project Folder

1. Ensure your folder structure is:
   ```
   BUZZBEE NATURALS/
   ├── index.html
   ├── product.html
   ├── about.html
   ├── contact.html
   ├── order.html
   ├── admin.html
   ├── app.py
   ├── requirements.txt
   ├── start.bat
   ├── start.ps1
   ├── README.md
   └── static/
       ├── style.css
       ├── logo.png (ADD YOUR LOGO HERE)
       ├── 1.jpg
       ├── 2.jpg
       ├── 3.jpg
       └── 4.jpg
   ```

### Step 3: Add Your Logo

1. Save your business logo as `static/logo.png`
   - Recommended size: 200x200px minimum
   - Recommended format: PNG with transparency
   - Alternative: Update `<img src="static/logo.png"...` to your filename in all HTML files

### Step 4: Install Dependencies

Open Command Prompt or PowerShell in the project folder:

```bash
pip install -r requirements.txt
```

This will install:
- Flask (web framework)
- Flask-CORS (for cross-origin requests)
- Requests (for API calls)

### Step 5: Run the Application

```bash
python app.py
```

You should see:
```
WARNING in app.run()
  * Running on http://127.0.0.1:5000
  * WARNING: This is a development server. Do not use it in production.
```

### Step 6: Access the Website

Open your browser and go to:
- **Main Site**: http://localhost:5000
- **Admin Dashboard**: http://localhost:5000/admin.html

---

## Features to Test

### 1. Navigation
- [ ] Home page loads with logo
- [ ] Navigation links work (Home, About, Products, Contact)
- [ ] Pages are mobile responsive

### 2. Logo Display
- [ ] Logo appears in header on all pages
- [ ] Logo looks good on mobile view

### 3. Honey Drips
- [ ] Honey drip decorations appear on each page
- [ ] They're positioned correctly (top-left, top-right, etc.)

### 4. Mobile Responsiveness
- [ ] Test on different screen sizes (use browser DevTools)
- [ ] Tablet view (768px)
- [ ] Mobile view (375px)
- [ ] All content is readable and properly laid out

### 5. Order Form
- Go to `/order.html`
- Fill in the form with test data:
  - Name: Test Customer
  - Email: test@example.com
  - Phone: 0700404773
  - Location: Nairobi
  - Product: Select any product
  - Quantity: 1
  - Delivery Date: Any future date
- Click "Place Order"
- Check that:
  - Success message appears
  - WhatsApp link opens (optional)
  - Admin dashboard shows the new order

### 6. Admin Dashboard
- Go to `/admin.html`
- Verify:
  - Stats display (Total Orders, Confirmed, Pending)
  - Order table shows all submitted orders
  - Page refreshes automatically every 30 seconds
  - Order details are correct

---

## Configuration

### Change WhatsApp Number

1. Open `app.py`
2. Find this line (around line 11):
   ```python
   ADMIN_WHATSAPP = "254700404773"
   ```
3. Replace with your WhatsApp number (without the + sign)

### Add More Products

1. Open `app.py`
2. Find the `add_default_products()` function
3. Add new products to the list:
   ```python
   products = [
       ("Product Name", price, "Description"),
       ("Raw Honey - 500ml", 1500, "Pure, unfiltered raw honey"),
   ]
   ```

### Customize Colors

1. Open `static/style.css`
2. Edit the color variables at the top:
   ```css
   :root {
       --dark-brown: #2B1B17;
       --honey-gold: #D49B00;
       --light-gold: #F0B823;
   }
   ```

### Change Business Info

Update these across files:
- Company Name: Search for "Buzz Bee Naturals"
- Email: Update in `contact.html` and forms
- Phone: Update WhatsApp number in code
- Address: Update in contact page

---

## Database Management

### View Database Directly

```bash
# Install SQLite Browser (optional)
python -m pip install db-browser-sqlite

# Or use command line
sqlite3 buzzbee_orders.db
```

### Reset Database

To start fresh with an empty database:

```bash
# Delete the database file
del buzzbee_orders.db

# Restart the app (it will recreate the database)
python app.py
```

### Backup Orders

```bash
# Make a copy of the database
copy buzzbee_orders.db buzzbee_orders_backup.db
```

---

## WhatsApp Integration Setup

### For Development (Current Setup)
- Orders are logged but not actually sent via WhatsApp
- Customers receive a link to WhatsApp chat

### For Production (Recommended: Twilio)

1. Sign up at https://www.twilio.com
2. Get your credentials (Account SID, Auth Token)
3. Get a WhatsApp-enabled Twilio number
4. Update `app.py`:
   ```python
   from twilio.rest import Client
   
   TWILIO_SID = 'your_account_sid'
   TWILIO_TOKEN = 'your_auth_token'
   TWILIO_NUMBER = 'whatsapp:+1234567890'
   ```

### For Production (Alternative: WhatsApp Cloud API)

1. Set up WhatsApp Business Account
2. Get API credentials
3. Update `send_whatsapp_message()` function in `app.py`

---

## Troubleshooting

### Python Not Found
```
'python' is not recognized as an internal or external command
```
**Solution**: Python not in PATH. Reinstall Python and check "Add Python to PATH" during installation.

### Port 5000 Already in Use
```
OSError: [Errno 10048] Only one usage of each socket address
```
**Solution**: Change port in `app.py`:
```python
app.run(debug=True, host='localhost', port=5001)  # Change 5000 to 5001
```

### Module Not Found
```
ModuleNotFoundError: No module named 'flask'
```
**Solution**: Install dependencies:
```bash
pip install -r requirements.txt
```

### Logo Not Showing
- Check file exists: `static/logo.png`
- Check file permissions (should be readable)
- Verify correct path in HTML: `<img src="static/logo.png"`

### Database Locked
- Close any other instances of the app
- Delete `.db-journal` file if it exists
- Restart the application

---

## Performance Tips

1. **Cache Images**: Use browser cache for static files
2. **Compress Images**: Keep image sizes under 500KB
3. **Minify CSS**: Remove comments for production
4. **Database Cleanup**: Archive old orders periodically

---

## Next Steps

### Phase 2 Features (Future)
- [ ] Payment integration (Mpesa, PayPal)
- [ ] User accounts and login
- [ ] Order tracking with real-time updates
- [ ] Email notifications
- [ ] Customer reviews
- [ ] Inventory management
- [ ] Email marketing integration

### Production Deployment
- Use Heroku, AWS, or DigitalOcean
- Set up SSL certificate (HTTPS)
- Configure custom domain
- Set up email notifications
- Implement proper authentication
- Monitor server logs

---

## Support & Contact

**Email**: buzzbeenaturals@gmail.com
**WhatsApp**: +254 700 404 773
**Website**: Will be available when deployed

---

## Document Version

- Version: 1.0
- Last Updated: June 2026
- Created for: Buzz Bee Naturals
