# Buzz Bee Naturals - E-Commerce Website

A complete e-commerce website for Buzz Bee Naturals with order management and WhatsApp integration.

## Features

✅ **Responsive Design** - Works on all devices (desktop, tablet, mobile)
✅ **Product Showcase** - Beautiful display of honey products
✅ **Order System** - Complete order form with validation
✅ **Database** - SQLite database for storing orders
✅ **WhatsApp Integration** - Automatic notifications to customers and admin
✅ **Admin Dashboard** - View and manage all orders
✅ **Mobile Responsive** - Optimized for all screen sizes

## Project Structure

```
BUZZBEE NATURALS/
├── index.html              # Home page
├── product.html            # Products page
├── about.html              # About page
├── contact.html            # Contact page
├── order.html              # Order page with form
├── admin.html              # Admin dashboard
├── app.py                  # Flask backend server
├── requirements.txt        # Python dependencies
├── static/
│   ├── style.css           # Main stylesheet
│   ├── logo.png            # Business logo
│   ├── 1.jpg               # Product image 1
│   ├── 2.jpg               # Product image 2
│   ├── 3.jpg               # Product image 3
│   └── 4.jpg               # Product image 4
└── buzzbee_orders.db       # SQLite database (auto-created)
```

## Setup Instructions

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)

### Installation

1. **Clone/Download the project**
   ```bash
   cd "BUZZBEE NATURALS"
   ```

2. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Add the logo image**
   - Save your business logo as `static/logo.png` (or your logo filename)
   - Update the HTML if using a different filename

4. **Run the Flask server**
   ```bash
   python app.py
   ```

5. **Access the website**
   - Open your browser and go to: `http://localhost:5000`
   - Admin dashboard: `http://localhost:5000/admin.html`

## Usage

### Customer Flow
1. Browse products on the website
2. Click on "Order" in navigation
3. Fill in order form with details
4. Submit order
5. Receive WhatsApp confirmation automatically

### Admin Features
- View all orders at `/admin.html`
- Monitor order statistics
- Track order status
- See customer details and contact information

## API Endpoints

### Create Order
```
POST /api/order
Content-Type: application/json

{
  "name": "Customer Name",
  "email": "email@example.com",
  "phone": "0700404773",
  "location": "Delivery Address",
  "product": "Product Name",
  "quantity": 1,
  "deliveryDate": "2026-06-20",
  "message": "Special instructions"
}
```

### Get All Orders
```
GET /api/orders
```

### Get Specific Order
```
GET /api/orders/{order_id}
```

### Update Order Status
```
PUT /api/orders/{order_id}/status
Content-Type: application/json

{
  "status": "confirmed|pending|shipped|delivered|cancelled"
}
```

### Get Products
```
GET /api/products
```

### Get Statistics
```
GET /api/stats
```

## WhatsApp Integration

The system automatically sends WhatsApp messages to:
1. **Customer** - Order confirmation with details
2. **Admin** - New order notification with customer info

WhatsApp Number: **+254 700 404 773**

### Sending WhatsApp Messages (Setup)

For production deployment, integrate with one of these services:

#### Option 1: Twilio (Recommended)
```python
from twilio.rest import Client

account_sid = 'YOUR_ACCOUNT_SID'
auth_token = 'YOUR_AUTH_TOKEN'
client = Client(account_sid, auth_token)

message = client.messages.create(
    body="Your order message",
    from_='whatsapp:+1234567890',
    to='whatsapp:+254700404773'
)
```

#### Option 2: WhatsApp Cloud API
- Set up WhatsApp Business Account
- Configure API credentials in `app.py`
- Update the `send_whatsapp_message()` function

#### Option 3: Simple HTTP Webhook
- Use services like Infobip or SMS Gateway
- Configure API endpoint and credentials

## Database Schema

### Orders Table
```sql
CREATE TABLE orders (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL,
  email TEXT NOT NULL,
  phone TEXT NOT NULL,
  location TEXT NOT NULL,
  product TEXT NOT NULL,
  quantity INTEGER NOT NULL,
  delivery_date TEXT NOT NULL,
  message TEXT,
  status TEXT DEFAULT 'pending',
  timestamp DATETIME DEFAULT CURRENT_TIMESTAMP,
  whatsapp_sent BOOLEAN DEFAULT 0
)
```

### Products Table
```sql
CREATE TABLE products (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL UNIQUE,
  price REAL NOT NULL,
  description TEXT,
  available BOOLEAN DEFAULT 1
)
```

## Customization

### Add New Products
Edit `app.py` and modify the `add_default_products()` function:

```python
products = [
    ("Your Product Name", price, "Description"),
]
```

### Change WhatsApp Number
Update `WHATSAPP_NUMBER` in `app.py`:
```python
WHATSAPP_NUMBER = "your_number_without_plus"
```

### Customize Styling
Edit `static/style.css` to modify:
- Colors
- Fonts
- Layout
- Responsive breakpoints

### Update Contact Info
- Email: Update in `contact.html`
- Phone: Update in `contact.html` and `app.py`
- Address: Update in relevant pages

## Deployment

### For Local Testing
```bash
python app.py
```

### For Production (Heroku)
1. Create `Procfile`:
   ```
   web: gunicorn app:app
   ```

2. Create `runtime.txt`:
   ```
   python-3.9.16
   ```

3. Deploy to Heroku:
   ```bash
   heroku login
   git push heroku main
   ```

### For Production (Other Servers)
- Use gunicorn: `gunicorn -w 4 -b 0.0.0.0:5000 app:app`
- Configure nginx/Apache as reverse proxy
- Enable HTTPS with SSL certificate

## Mobile Responsive Breakpoints

- **Desktop**: 1200px and above
- **Tablet**: 641px - 1199px
- **Mobile**: 640px and below

All pages are fully responsive and tested on various devices.

## Troubleshooting

### Port Already in Use
If port 5000 is in use, change it in `app.py`:
```python
app.run(debug=True, host='localhost', port=5001)
```

### Database Issues
Delete `buzzbee_orders.db` to reset the database:
```bash
rm buzzbee_orders.db
python app.py
```

### WhatsApp Messages Not Sending
1. Check WhatsApp API credentials
2. Verify phone number format (+254...)
3. Check API rate limits
4. Review server logs for errors

### Images Not Loading
1. Ensure image files exist in `static/` folder
2. Check file permissions
3. Verify correct file paths in HTML/CSS

## Support

For issues or questions:
- Email: buzzbeenaturals@gmail.com
- WhatsApp: +254 700 404 773

## License

© 2026 Buzz Bee Naturals. All rights reserved.

---

**Last Updated**: June 2026
**Version**: 1.0.0
