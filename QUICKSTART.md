# ⚡ Quick Start - Get Running in 60 Seconds

## 🚀 For Windows Users (Fastest)

### Option 1: Just Click & Go
1. **Double-click** `start.bat`
2. **Wait** for installation to finish
3. **Browser opens** automatically to http://localhost:5000
4. Done! ✅

### Option 2: PowerShell
```powershell
# Right-click start.ps1 → Run with PowerShell
# Allow execution if prompted
# Browser opens automatically
```

---

## 🔧 For Mac/Linux Users

```bash
# Open terminal in project folder
pip install -r requirements.txt
python app.py

# Open browser to http://localhost:5000
```

---

## ✅ What You Should See

```
✓ Home page with your company logo
✓ Navigation menu (Home, About, Products, Contact)
✓ Professional honey-themed design
✓ All pages mobile responsive
✓ Honey drip decorations on each page
```

---

## 📋 Before You Start

1. **Make sure you have Python installed**
   ```bash
   python --version  # Should be 3.8 or higher
   ```

2. **Add your logo**
   - Save your logo as `static/logo.png`
   - Size: 200x200px or larger (PNG recommended)

3. **That's it!** Everything else is included

---

## 🌐 Test the Features

### From Home Page
- ✅ Click navigation links (all should work)
- ✅ View responsive design (resize browser window)
- ✅ See honey drip decoration

### Order Page (`/order.html`)
1. Fill in order form:
   - Name, Email, Phone
   - Location, Product, Quantity
   - Delivery Date
2. Click "Place Order"
3. See success message ✅
4. Check admin dashboard for new order

### Admin Dashboard (`/admin.html`)
- View all orders
- See statistics
- Monitor customer information
- Page auto-refreshes every 30 seconds

### Contact Page
- Click WhatsApp link to message +254 700 404 773

---

## 🔑 Key URLs

| Page | URL |
|------|-----|
| Home | http://localhost:5000 |
| Products | http://localhost:5000/product.html |
| About | http://localhost:5000/about.html |
| Contact | http://localhost:5000/contact.html |
| Order | http://localhost:5000/order.html |
| Admin | http://localhost:5000/admin.html |

---

## 🛠️ Customization (Easy)

### Change WhatsApp Number
Edit in two places:
1. `app.py` - Line 11: `ADMIN_WHATSAPP = "your_number"`
2. `contact.html` - WhatsApp link with your number

### Change Business Name
Search and replace "Buzz Bee Naturals" with your company name

### Change Colors
Edit `static/style.css` at the top:
```css
:root {
    --dark-brown: #2B1B17;      /* Change these */
    --honey-gold: #D49B00;
    --light-gold: #F0B823;
}
```

### Add Products
Edit `app.py` function `add_default_products()`:
```python
products = [
    ("Your Product Name", 1500, "Description"),
]
```

---

## ❓ Troubleshooting

### "Python not found"
- Reinstall Python from https://www.python.org/
- Make sure to check "Add Python to PATH"

### "Port 5000 already in use"
- Open `app.py`
- Change `port=5000` to `port=5001`

### "ModuleNotFoundError: No module named 'flask'"
```bash
pip install -r requirements.txt
```

### Logo not showing
- File must be named `static/logo.png`
- Check file permissions (should be readable)

---

## 📖 More Information

- **Setup Details**: See `SETUP.md`
- **All Features**: See `FEATURES.md`
- **Full Docs**: See `README.md`

---

## 🎉 You're Done!

Your website is now running with:
- ✅ Responsive design (mobile, tablet, desktop)
- ✅ Professional branding with logo and honey drips
- ✅ Complete order system with database
- ✅ WhatsApp integration
- ✅ Admin dashboard
- ✅ Production-ready code

### Next Steps:
1. Customize colors and text
2. Add your logo
3. Update WhatsApp number
4. Test all pages
5. Deploy to production

---

## 📞 Contact

- **WhatsApp**: +254 700 404 773
- **Email**: buzzbeenaturals@gmail.com

---

**Happy selling! 🐝🍯**
