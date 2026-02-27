# CAMC Website - Deployment Guide
## Christ Apostolic Mission Church Worldwide

---

## 📁 WHAT'S INCLUDED

```
camc-website/
├── index.php              ← Homepage
├── .htaccess              ← Security config
├── pages/
│   ├── about.php          ← Church history
│   ├── gallery.php        ← Photo gallery (all 13 event photos)
│   ├── events.php         ← Events page
│   ├── sermons.php        ← Sermons page
│   ├── leadership.php     ← Leadership page
│   ├── branches.php       ← Branch network
│   └── contact.php        ← Contact form
├── admin/
│   ├── login.php          ← Admin login
│   ├── logout.php         ← Logout handler
│   ├── super/             ← Super Admin panel
│   │   ├── dashboard.php
│   │   ├── gallery.php    ← Upload & manage photos
│   │   ├── sermons.php
│   │   ├── events.php
│   │   ├── branches.php
│   │   └── users.php
│   └── branch/            ← Branch Admin panel
│       ├── dashboard.php
│       ├── gallery.php
│       ├── sermons.php
│       └── events.php
├── assets/
│   ├── css/style.css
│   ├── js/main.js
│   └── images/            ← All 13 event photos + gallery uploads
└── includes/
    ├── header.php
    ├── footer.php
    └── data/              ← JSON data storage (protected)
```

---

## 🚀 HOW TO UPLOAD TO cPANEL (REGISTERAM)

### METHOD 1: File Manager (Easiest)

1. **Login to your cPanel** at `yourdomain.com/cpanel` or `registeram.com/cpanel`

2. **Go to File Manager** (find it in the Files section)

3. **Navigate to `public_html`** (this is your website root)

4. **Upload the ZIP file:**
   - Click **Upload** button
   - Select `camc-website.zip`
   - Wait for upload to complete

5. **Extract the ZIP:**
   - Right-click `camc-website.zip`
   - Click **Extract**
   - Extract to `/public_html/` (NOT into a subfolder, or the URL will be `yourdomain.com/camc-website/`)

6. **Check permissions:**
   - Right-click `assets/images/gallery` folder → Permissions → Set to **755**
   - Right-click `includes/data` folder → Permissions → Set to **755**

7. **Visit your site:** `https://yourdomain.com`

---

### METHOD 2: FTP (FileZilla)

1. **Download FileZilla** (free): https://filezilla-project.org

2. **Get FTP credentials** from cPanel:
   - cPanel → FTP Accounts → Create new or use main account
   - Note: Host, Username, Password, Port (usually 21)

3. **Connect in FileZilla:**
   - Host: `ftp.yourdomain.com`
   - Username: your FTP username
   - Password: your FTP password
   - Port: 21

4. **Upload files:**
   - Left panel (your computer): Navigate to the `camc-website` folder
   - Right panel (server): Navigate to `public_html`
   - Select all files in `camc-website` folder and drag to `public_html`

---

## 🔐 ADMIN LOGIN CREDENTIALS

**Change these IMMEDIATELY after deployment!**

| Username | Password | Role | Access |
|----------|----------|------|--------|
| superadmin | camc2026!super | Super Admin | Full access |
| branch1 | camc2026!branch1 | Branch Admin | Abule-Egba |
| branch2 | camc2026!branch2 | Branch Admin | Mushin |
| branch3 | camc2026!branch3 | Branch Admin | Ibadan |

**To change passwords:** Edit `admin/login.php`, find the `$users` array, update passwords.

**Admin URL:** `https://yourdomain.com/admin/login.php`

---

## 📸 UPLOADING MORE PHOTOS

1. Login as Super Admin or Branch Admin
2. Click **Gallery** in the sidebar
3. Fill in Event Name, Branch, Caption
4. Click the upload zone and select your photos
5. Click **Upload Photos**
6. Photos appear instantly on the public gallery page

---

## ✅ REQUIREMENTS

- PHP 7.4+ (most cPanel hosts support this)
- No MySQL database needed (uses JSON files)
- The `includes/data/` folder must be writable (chmod 755)
- The `assets/images/gallery/` folder must be writable (chmod 755)

---

## 🔧 TROUBLESHOOTING

**Photos not uploading?**
→ Check folder permissions: `assets/images/gallery` should be 755 or 777

**Contact form not working?**
→ Your host may require SMTP. Consider adding PHPMailer to `pages/contact.php`

**Blank page / PHP errors?**
→ Check PHP version in cPanel → MultiPHP Manager → Set to PHP 7.4 or 8.x

**Can't access admin?**
→ Ensure you're going to `/admin/login.php` not `/admin/`

---

## 📞 CHURCH CONTACT
1/5 CAMC Salvation Street, Off Yisa Oladimeji Street  
U-Turn Bus-Stop, Abule-Egba, Lagos State  
Tel: 07048700005
