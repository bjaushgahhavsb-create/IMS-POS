# 🏪 IMS POS Enterprise System v2.0
### Complete Inventory Management & Point of Sale — ASP.NET Core 8

---

## 🚀 QUICK START (Visual Studio 2022)

### Step 1 — Prerequisites
- Visual Studio 2022 (any edition)
- .NET 8 SDK
- SQL Server / SQL Express / LocalDB (any one)

### Step 2 — Choose Your Database
Open `src/IMS_POS.Web/appsettings.json` and change `"ActiveConnection"` to one of:

```json
"ActiveConnection": "LocalDB"        // Visual Studio default (recommended)
"ActiveConnection": "SqlExpress"     // SQL Server Express
"ActiveConnection": "SqlServer"      // Full SQL Server (Windows Auth)
"ActiveConnection": "SqlServerAuth"  // Full SQL Server (SA login) — edit password
```

If using **SqlServerAuth**, also update the password:
```json
"SqlServerAuth": "Server=localhost;Database=IMS_POS_DB;User Id=sa;Password=YOUR_PASSWORD;..."
```

### Step 3 — Open Solution
```
Double-click:  IMS_POS.sln
```

### Step 4 — Apply Database Migration

Open **Package Manager Console** (Tools → NuGet → Package Manager Console):
```powershell
# Set default project to Infrastructure:
Add-Migration InitialCreate -Project IMS_POS.Infrastructure -StartupProject IMS_POS.Web
Update-Database -Project IMS_POS.Infrastructure -StartupProject IMS_POS.Web
```

**OR** use **Terminal** / Developer PowerShell:
```bash
cd src/IMS_POS.Web
dotnet ef migrations add InitialCreate --project ../IMS_POS.Infrastructure
dotnet ef database update --project ../IMS_POS.Infrastructure
```

### Step 5 — Run!
Press **F5** or click ▶ **Run** in Visual Studio.

The app will automatically:
- ✅ Create the database
- ✅ Seed demo data (products, customers, suppliers)
- ✅ Create all user accounts

---

## 🔑 Demo Login Accounts

| Role | Email | Password |
|------|-------|----------|
| **Super Admin** | superadmin@ims.com | Admin@123456 |
| **Shop Admin** | admin@demo.com | Admin@123456 |
| **Cashier** | cashier@demo.com | Admin@123456 |

---

## 🏗️ Architecture

```
IMS_POS/
├── src/
│   ├── IMS_POS.Core/              ← Domain Layer
│   │   ├── Entities/              ← All database models
│   │   └── Interfaces/            ← Repository & Service contracts
│   │
│   ├── IMS_POS.Infrastructure/    ← Data Layer
│   │   ├── Data/                  ← DbContext + Seeder
│   │   ├── Migrations/            ← EF Core migrations
│   │   ├── Repositories/          ← Generic Repository + UoW
│   │   └── Services/              ← Audit, Inventory, Dashboard, Export...
│   │
│   └── IMS_POS.Web/               ← Presentation Layer (MVC)
│       ├── Areas/SuperAdmin/      ← Super Admin panel
│       ├── Controllers/           ← All MVC controllers
│       ├── Views/                 ← Razor views
│       └── wwwroot/               ← CSS, JS, images
└── IMS_POS.sln
```

---

## ✨ Features

### 🔐 Authentication & Authorization
- ASP.NET Identity with JWT support
- Dynamic Role & Permission system
- Branch-wise access control
- Audit logging (who did what, when, from where)

### 🏢 Multi-Tenant Architecture
- One system → multiple shops
- Each shop → multiple branches
- Each branch → multiple warehouses
- Branch-wise inventory, sales, purchases, expenses

### 🛒 Point of Sale (POS)
- Fast barcode scanner support
- Product search by name/SKU/barcode
- Split payments (Cash + Card + Bank + JazzCash)
- Hold & resume invoices
- Thermal receipt printing (80mm)
- Discount per item & cart-level discount
- Tax calculation

### 📦 Inventory Management
- Products with variants (Size, Color, Storage...)
- FEFO batch tracking (pharmacy ready)
- Expiry date tracking
- Warehouse-to-branch stock transfer
- Low stock alerts
- Auto SKU generation
- Barcode & QR code support

### 💰 Transactions
- Purchase invoices with batch/expiry
- Sale invoices (retail + wholesale)
- Sale & purchase returns
- Partial payments & due tracking
- Customer/Supplier ledgers

### 📊 Reports
- Sales Report (filterable, exportable to Excel)
- Stock Report
- Profit & Loss
- Customer Due Report
- Supplier Payable Report
- Audit Logs

### 🎨 UI/UX
- Dark Mode / Light Mode (toggle)
- Fully responsive (Mobile + Tablet + Desktop)
- Luxury enterprise design
- Fast navigation
- Real-time toast notifications

---

## ⚙️ Configuration

### Connection Strings (appsettings.json)
```json
"ConnectionStrings": {
  "LocalDB":      "Server=(localdb)\\MSSQLLocalDB;Database=IMS_POS_DB;...",
  "SqlExpress":   "Server=localhost\\SQLEXPRESS;Database=IMS_POS_DB;...",
  "SqlServer":    "Server=localhost;Database=IMS_POS_DB;...",
  "SqlServerAuth":"Server=localhost;Database=IMS_POS_DB;User Id=sa;Password=..."
},
"ActiveConnection": "LocalDB"   ← change this
```

### App Settings
```json
"AppSettings": {
  "DefaultCurrency": "PKR",
  "DefaultCurrencySymbol": "Rs.",
  "DefaultLanguage": "en",
  "PageSize": 25,
  "InvoicePrefix": "INV",
  "PurchasePrefix": "PUR"
}
```

---

## 🏭 Industry Support
This system works for:
- 💊 Pharmacies (FEFO, batch, expiry)
- 🛒 Grocery & Supermarkets
- 📱 Mobile & Electronics shops
- 👗 Clothing stores
- 🔧 Hardware stores
- 🏭 Wholesale businesses
- 🏪 Multi-branch retail

---

## 📋 Modules Checklist

| Module | Status |
|--------|--------|
| Authentication / Authorization | ✅ |
| Dashboard with Analytics | ✅ |
| Product Management | ✅ |
| Category / Brand / Unit | ✅ |
| Warehouse Management | ✅ |
| Stock Transfer | ✅ |
| POS System | ✅ |
| Sales Invoices | ✅ |
| Purchase Invoices | ✅ |
| Sale Returns | ✅ |
| Purchase Returns | ✅ |
| Customer Management | ✅ |
| Supplier Management | ✅ |
| Customer Ledger | ✅ |
| Supplier Ledger | ✅ |
| Expense Management | ✅ |
| Sales Report (Excel Export) | ✅ |
| Stock Report | ✅ |
| Profit & Loss | ✅ |
| Audit Logs | ✅ |
| User Management | ✅ |
| Dynamic Roles & Permissions | ✅ |
| Multi-Branch | ✅ |
| Multi-Tenant / Multi-Shop | ✅ |
| Super Admin Panel | ✅ |
| Dark / Light Theme | ✅ |
| Thermal Receipt Print | ✅ |
| Barcode Scanner Support | ✅ |
| FEFO Batch Tracking | ✅ |
| Low Stock Alerts | ✅ |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | ASP.NET Core 8 MVC |
| ORM | Entity Framework Core 8 |
| Database | SQL Server / LocalDB |
| Auth | ASP.NET Identity |
| Architecture | Clean Architecture + Repository + UoW |
| Frontend | Bootstrap 5 + Custom CSS |
| Charts | Chart.js |
| Icons | Font Awesome 6 |
| Excel Export | ClosedXML |
| Notifications | SignalR (ready to extend) |

---

## 📞 Support
Developed for Pakistani retail businesses.
Default currency: **PKR (Rs.)**
Default locale: **Pakistan**

---
*IMS POS Enterprise v2.0 — Built with ❤️*
