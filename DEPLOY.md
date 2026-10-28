# Panel Sell PHP Store — Deployment Guide

## Current Status

| Item | Status |
|------|--------|
| Site code | Complete |
| Files uploaded to InfinityFree | Done |
| Domain `solaymanxcheat.rf.gd` | Not active (HTTP 000) |
| MySQL DB | Configured (user: if0_43202417) |
| RupantorPay integration | Complete |

## Problem: Domain Not Active

`solaymanxcheat.rf.gd` returns **HTTP 000** — InfinityFree's server is not responding to requests for this domain.

**I cannot activate this domain.** Only you can, through the InfinityFree Client Area.

### Steps to activate (you must do this):

1. Go to https://clientarea.epizy.com/
2. Login with your InfinityFree credentials
3. Go to **Addon Domains**
4. Check if `solaymanxcheat.rf.gd` is listed
   - If NOT listed: Add it with Document Root `htdocs/solaymanxcheat.rf.gd/`
   - If listed but not active: Edit it, set Document Root to `htdocs/solaymanxcheat.rf.gd/`
5. **Wait 30 minutes to 24 hours** for DNS propagation
6. Visit `http://solaymanxcheat.rf.gd/` — your site should load

## Alternative: Use Default Domain

Your default domain `if0_43202417.rf.gd` IS responding (HTTP 200) but shows InfinityFree's error page. This means the domain configuration needs fixing too. In the Client Area, make sure your hosting account is properly linked to this domain.

## Environment Variables

Copy `.env.example` to `.env` and fill in your values:

```
DB_DRIVER=mysql
DB_HOST=sql304.infinityfree.com
DB_NAME=if0_43202417
DB_USER=if0_43202417
DB_PASS=your_password
RUPANTOR_API_KEY=your_key
```

On InfinityFree, set these in the Client Area → PHP → PHP Variables, or in your `.env` file.

## Files Already Uploaded to Server

All files are in `htdocs/solaymanxcheat.rf.gd/`:
- `api.php` — API endpoints (payment_status, deposit_rupantor, etc.)
- `index.php` — Main frontend
- `config.php` — Configuration (updated with env var support)
- `lib.php` — Core library (db, auth, migrations)
- `auth.php` — Authentication
- `checkout.php` — Checkout page
- `admin.php` — Admin panel
- `assets/app.js` — Frontend JS (includes payment polling)
- `assets/style.css` — Styles
- `db_test.php` — Database connection test

## Testing

Once domain is active, visit:
- `http://solaymanxcheat.rf.gd/` — Main site
- `http://solaymanxcheat.rf.gd/db_test.php` — Test MySQL connection
- `http://solaymanxcheat.rf.gd/api/payment_status?code=XXX` — Test payment status API

## If Domain Never Activates

Consider alternative free PHP hosting:
- **000webhost.com** — PHP + MySQL, instant setup
- **AwardSpace.com** — PHP + MySQL, instant setup  
- **FreeHostia.com** — PHP + MySQL, instant setup

Upload the same files and update `config.php` with new DB credentials.
