# 🎯 STOCKI - Complete Development Specification & Build Instructions

## 📋 PROJECT OVERVIEW

**Project Name:** Stocki (Ultimate Stock Management Application)
**Technology Stack:** C# .NET Framework 4.8, WPF, SQL Server/SQLite
**Target Platform:** Windows Desktop (macOS-inspired design)
**Status:** New Project - Ready for Full Development
**Deadline:** As needed
**Budget:** Open

---

## 🎨 DESIGN PHILOSOPHY

### UI/UX Design
- **Theme:** macOS-inspired (Apple design language)
- **Color Palette:** 
  - Primary: Silver/Gray (#F5F5F5, #E8E8E8)
  - Accent: Blue (#007AFF or similar)
  - Dark Mode: Dark Gray (#1E1E1E)
  - Text: Black (#000000) / White (#FFFFFF)
- **Typography:** Use system fonts similar to San Francisco
- **Components:** Rounded corners, subtle shadows, smooth animations
- **Responsiveness:** Adapt to different screen resolutions
- **Accessibility:** Dark mode support, keyboard shortcuts, high contrast options

### User Experience
- Minimize clicks and maximize productivity
- Keyboard shortcuts for all major functions
- Command palette (Cmd+K style)
- Drag-and-drop functionality
- Real-time data updates
- Intuitive navigation hierarchy

---

## 🏗️ PROJECT STRUCTURE & ARCHITECTURE

### Layered Architecture
```
Presentation Layer (WPF UI)
    ↓
Business Logic Layer (Services)
    ↓
Data Access Layer (Repositories)
    ↓
Database Layer (SQL Server/SQLite)
```

### Solution Structure
```
StockMaster/
├── Source/
│   ├── Stocki.UI/
│   │   ├── App.xaml
│   │   ├── App.xaml.cs
│   │   ├── MainWindow.xaml
│   │   ├── MainWindow.xaml.cs
│   │   ├── Views/
│   │   │   ├── Dashboard/
│   │   │   ├── Inventory/
│   │   │   ├── POS/
│   │   │   ├── Customers/
│   │   │   ├── Reports/
│   │   │   ├── Users/
│   │   │   └── Settings/
│   │   ├── ViewModels/
│   │   ├── Resources/
│   │   │   ├── Styles.xaml
│   │   │   ├── Colors.xaml
│   │   │   ├── Themes/
│   │   │   │   ├── LightTheme.xaml
│   │   │   │   └── DarkTheme.xaml
│   │   │   └── Icons/
│   │   ├── Converters/
│   │   ├── Behaviors/
│   │   └── Stocki.UI.csproj
│   ├── Stocki.Core/
│   │   ├── Models/
│   │   │   ├── Product.cs
│   │   │   ├── Customer.cs
│   │   │   ├── Sale.cs
│   │   │   ├── SaleItem.cs
│   │   │   ├── Inventory.cs
│   │   │   ├── StockMovement.cs
│   │   │   ├── User.cs
│   │   │   ├── Role.cs
│   │   │   ├── Location.cs
│   │   │   ├── Supplier.cs
│   │   │   ├── PurchaseOrder.cs
│   │   │   ├── Category.cs
│   │   │   ├── Report.cs
│   │   │   └── [Other Models]
│   │   ├── Services/
│   │   │   ├── ProductService.cs
│   │   │   ├── InventoryService.cs
│   │   │   ├── SalesService.cs
│   │   │   ├── CustomerService.cs
│   │   │   ├── UserService.cs
│   │   │   ├── ReportService.cs
│   │   │   ├── AuthenticationService.cs
│   │   │   ├── BackupService.cs
│   │   │   └── [Other Services]
│   │   ├── Interfaces/
│   │   │   ├── IProductService.cs
│   │   │   ├── IInventoryService.cs
│   │   │   └── [Service Interfaces]
│   │   ├── Utilities/
│   │   │   ├── ValidationHelper.cs
│   │   │   ├── DateTimeHelper.cs
│   │   │   ├── CurrencyHelper.cs
│   │   │   └── [Helper Classes]
│   │   └── Stocki.Core.csproj
│   ├── Stocki.Data/
│   │   ├── StockiDbContext.cs
│   │   ├── Configurations/
│   │   │   ├── ProductConfiguration.cs
│   │   │   ├── CustomerConfiguration.cs
│   │   │   └── [Entity Configurations]
│   │   ├── Repositories/
│   │   │   ├── IRepository.cs
│   │   │   ├── Repository.cs
│   │   │   ├── ProductRepository.cs
│   │   │   ├── InventoryRepository.cs
│   │   │   ├── SalesRepository.cs
│   │   │   └── [Specific Repositories]
│   │   ├── Migrations/
│   │   │   ├── [Migration files]
│   │   │   └── Configuration.cs
│   │   ├── Entities/
│   │   │   ├── [Mirror of Core/Models]
│   │   │   └── Configurations/
│   │   └── Stocki.Data.csproj
│   ├── Stocki.Barcode/
│   │   ├── Generators/
│   │   │   ├── BarcodeGenerator.cs
│   │   │   ├── EAN13Generator.cs
│   │   │   ├── Code128Generator.cs
│   │   │   ├── QRCodeGenerator.cs
│   │   │   └── BatchBarcodeGenerator.cs
│   │   ├── Scanners/
│   │   │   ├── ScannerBase.cs
│   │   │   ├── USBScannerHandler.cs
│   │   │   ├── WirelessScannerHandler.cs
│   │   │   └── SimulatorScanner.cs
│   │   ├── Processors/
│   │   │   └── BarcodeProcessor.cs
│   │   └── Stocki.Barcode.csproj
│   ├── Stocki.Reporting/
│   │   ├── Generators/
│   │   │   ├── SalesReportGenerator.cs
│   │   │   ├── InventoryReportGenerator.cs
│   │   │   ├── CustomerReportGenerator.cs
│   │   │   ├── ProfitLossReportGenerator.cs
│   │   │   └── StockMovementReportGenerator.cs
│   │   ├── Templates/
│   │   │   ├── ReportTemplate.xaml
│   │   │   └── [Other Templates]
│   │   ├── Exporters/
│   │   │   ├── ExcelExporter.cs
│   │   │   ├── PDFExporter.cs
│   │   │   └── CSVExporter.cs
│   │   └── Stocki.Reporting.csproj
│   ├── Stocki.Printing/
│   │   ├── Printers/
│   │   │   ├── PrinterBase.cs
│   │   │   ├── ThermalPrinter.cs
│   │   │   ├── InkjetPrinter.cs
│   │   │   └── LaserPrinter.cs
│   │   ├── Templates/
│   │   │   ├── InvoiceTemplate.xaml
│   │   │   ├── BarcodeLabel.xaml
│   │   │   ├── ReceiptTemplate.xaml
│   │   │   └── CustomTemplate.xaml
│   │   ├── PrintService.cs
│   │   └── Stocki.Printing.csproj
│   └── Stocki.Api/ (Optional - Future)
│       ├── Controllers/
│       ├── Models/
│       └── Stocki.Api.csproj
├── Tests/
│   ├── Stocki.Core.Tests/
│   │   ├── Services/
│   │   └── Utilities/
│   ├── Stocki.Data.Tests/
│   │   ├── Repositories/
│   │   └── StockiDbContext.Tests.cs
│   └── Stocki.UI.Tests/
│       └── ViewModels/
├── Docs/
│   ├── USER_GUIDE.md
│   ├── DEVELOPER_GUIDE.md
│   ├── DATABASE_SCHEMA.md
│   ├── API_DOCUMENTATION.md
│   └── DEPLOYMENT.md
├── StockMaster.sln
└── README.md
```

---

## 🗄️ DATABASE SCHEMA

### Key Tables

#### **Products**
```sql
CREATE TABLE Products (
    ProductId INT PRIMARY KEY IDENTITY(1,1),
    Name NVARCHAR(255) NOT NULL,
    SKU NVARCHAR(100) UNIQUE NOT NULL,
    Barcode NVARCHAR(100) UNIQUE,
    Description NVARCHAR(MAX),
    CategoryId INT,
    SupplierId INT,
    Price DECIMAL(18,2) NOT NULL,
    CostPrice DECIMAL(18,2),
    ReorderLevel INT,
    ReorderQuantity INT,
    UnitOfMeasure NVARCHAR(50),
    ExpiryDate DATETIME,
    CreatedAt DATETIME DEFAULT GETDATE(),
    UpdatedAt DATETIME,
    IsActive BIT DEFAULT 1,
    CreatedBy NVARCHAR(255),
    UpdatedBy NVARCHAR(255)
);
```

#### **Inventory**
```sql
CREATE TABLE Inventory (
    InventoryId INT PRIMARY KEY IDENTITY(1,1),
    ProductId INT NOT NULL,
    LocationId INT NOT NULL,
    QuantityOnHand INT NOT NULL,
    QuantityReserved INT DEFAULT 0,
    QuantityAvailable INT,
    LastCountDate DATETIME,
    LastMovementDate DATETIME,
    FOREIGN KEY (ProductId) REFERENCES Products(ProductId),
    FOREIGN KEY (LocationId) REFERENCES Locations(LocationId)
);
```

#### **Customers**
```sql
CREATE TABLE Customers (
    CustomerId INT PRIMARY KEY IDENTITY(1,1),
    Name NVARCHAR(255) NOT NULL,
    Email NVARCHAR(255),
    Phone NVARCHAR(20),
    Address NVARCHAR(MAX),
    City NVARCHAR(100),
    PostalCode NVARCHAR(20),
    Country NVARCHAR(100),
    CustomerGroupId INT,
    CreditLimit DECIMAL(18,2),
    OutstandingBalance DECIMAL(18,2),
    LoyaltyPoints INT DEFAULT 0,
    DateOfBirth DATETIME,
    TaxId NVARCHAR(50),
    CreatedAt DATETIME DEFAULT GETDATE(),
    UpdatedAt DATETIME,
    IsActive BIT DEFAULT 1,
    FOREIGN KEY (CustomerGroupId) REFERENCES CustomerGroups(CustomerGroupId)
);
```

#### **Sales**
```sql
CREATE TABLE Sales (
    SaleId INT PRIMARY KEY IDENTITY(1,1),
    SaleNumber NVARCHAR(50) UNIQUE NOT NULL,
    SaleDate DATETIME DEFAULT GETDATE(),
    CustomerId INT,
    LocationId INT NOT NULL,
    UserId INT NOT NULL,
    SubTotal DECIMAL(18,2) NOT NULL,
    DiscountAmount DECIMAL(18,2),
    DiscountPercentage DECIMAL(5,2),
    TaxAmount DECIMAL(18,2),
    TotalAmount DECIMAL(18,2) NOT NULL,
    PaymentMethod NVARCHAR(50),
    PaymentStatus NVARCHAR(50),
    OrderStatus NVARCHAR(50),
    Notes NVARCHAR(MAX),
    CreatedAt DATETIME DEFAULT GETDATE(),
    FOREIGN KEY (CustomerId) REFERENCES Customers(CustomerId),
    FOREIGN KEY (LocationId) REFERENCES Locations(LocationId),
    FOREIGN KEY (UserId) REFERENCES Users(UserId)
);
```

#### **SalesItems**
```sql
CREATE TABLE SalesItems (
    SalesItemId INT PRIMARY KEY IDENTITY(1,1),
    SaleId INT NOT NULL,
    ProductId INT NOT NULL,
    Quantity INT NOT NULL,
    UnitPrice DECIMAL(18,2) NOT NULL,
    DiscountAmount DECIMAL(18,2),
    TaxAmount DECIMAL(18,2),
    LineTotal DECIMAL(18,2) NOT NULL,
    FOREIGN KEY (SaleId) REFERENCES Sales(SaleId),
    FOREIGN KEY (ProductId) REFERENCES Products(ProductId)
);
```

#### **StockMovements**
```sql
CREATE TABLE StockMovements (
    MovementId INT PRIMARY KEY IDENTITY(1,1),
    ProductId INT NOT NULL,
    LocationId INT NOT NULL,
    MovementType NVARCHAR(50), -- 'In', 'Out', 'Transfer', 'Adjustment'
    Quantity INT NOT NULL,
    Reference NVARCHAR(100),
    ReferencedEntityId INT,
    Reason NVARCHAR(255),
    Notes NVARCHAR(MAX),
    CreatedBy NVARCHAR(255),
    CreatedAt DATETIME DEFAULT GETDATE(),
    FOREIGN KEY (ProductId) REFERENCES Products(ProductId),
    FOREIGN KEY (LocationId) REFERENCES Locations(LocationId)
);
```

#### **Users**
```sql
CREATE TABLE Users (
    UserId INT PRIMARY KEY IDENTITY(1,1),
    Username NVARCHAR(100) UNIQUE NOT NULL,
    PasswordHash NVARCHAR(255) NOT NULL,
    Email NVARCHAR(255),
    FullName NVARCHAR(255),
    Phone NVARCHAR(20),
    RoleId INT NOT NULL,
    LocationId INT,
    IsActive BIT DEFAULT 1,
    LastLoginAt DATETIME,
    CreatedAt DATETIME DEFAULT GETDATE(),
    UpdatedAt DATETIME,
    FOREIGN KEY (RoleId) REFERENCES Roles(RoleId),
    FOREIGN KEY (LocationId) REFERENCES Locations(LocationId)
);
```

#### **Roles**
```sql
CREATE TABLE Roles (
    RoleId INT PRIMARY KEY IDENTITY(1,1),
    Name NVARCHAR(100) UNIQUE NOT NULL,
    Description NVARCHAR(MAX),
    CreatedAt DATETIME DEFAULT GETDATE()
);
```

#### **RolePermissions**
```sql
CREATE TABLE RolePermissions (
    RolePermissionId INT PRIMARY KEY IDENTITY(1,1),
    RoleId INT NOT NULL,
    PermissionKey NVARCHAR(255) NOT NULL,
    FOREIGN KEY (RoleId) REFERENCES Roles(RoleId)
);
```

#### **Locations**
```sql
CREATE TABLE Locations (
    LocationId INT PRIMARY KEY IDENTITY(1,1),
    Name NVARCHAR(255) NOT NULL,
    Address NVARCHAR(MAX),
    City NVARCHAR(100),
    PostalCode NVARCHAR(20),
    Phone NVARCHAR(20),
    Email NVARCHAR(255),
    IsHeadquarters BIT DEFAULT 0,
    IsActive BIT DEFAULT 1,
    CreatedAt DATETIME DEFAULT GETDATE()
);
```

#### **Suppliers**
```sql
CREATE TABLE Suppliers (
    SupplierId INT PRIMARY KEY IDENTITY(1,1),
    Name NVARCHAR(255) NOT NULL,
    Email NVARCHAR(255),
    Phone NVARCHAR(20),
    Address NVARCHAR(MAX),
    City NVARCHAR(100),
    PostalCode NVARCHAR(20),
    ContactPerson NVARCHAR(255),
    PaymentTerms NVARCHAR(100),
    IsActive BIT DEFAULT 1,
    CreatedAt DATETIME DEFAULT GETDATE()
);
```

#### **PurchaseOrders**
```sql
CREATE TABLE PurchaseOrders (
    PurchaseOrderId INT PRIMARY KEY IDENTITY(1,1),
    PONumber NVARCHAR(50) UNIQUE NOT NULL,
    SupplierId INT NOT NULL,
    OrderDate DATETIME DEFAULT GETDATE(),
    ExpectedDeliveryDate DATETIME,
    ActualDeliveryDate DATETIME,
    Status NVARCHAR(50),
    SubTotal DECIMAL(18,2),
    TaxAmount DECIMAL(18,2),
    TotalAmount DECIMAL(18,2),
    Notes NVARCHAR(MAX),
    CreatedBy NVARCHAR(255),
    FOREIGN KEY (SupplierId) REFERENCES Suppliers(SupplierId)
);
```

#### **Categories**
```sql
CREATE TABLE Categories (
    CategoryId INT PRIMARY KEY IDENTITY(1,1),
    Name NVARCHAR(255) NOT NULL,
    Description NVARCHAR(MAX),
    ParentCategoryId INT,
    IsActive BIT DEFAULT 1
);
```

#### **ActivityLog**
```sql
CREATE TABLE ActivityLog (
    LogId INT PRIMARY KEY IDENTITY(1,1),
    UserId INT,
    Action NVARCHAR(255),
    EntityType NVARCHAR(100),
    EntityId INT,
    OldValue NVARCHAR(MAX),
    NewValue NVARCHAR(MAX),
    CreatedAt DATETIME DEFAULT GETDATE(),
    FOREIGN KEY (UserId) REFERENCES Users(UserId)
);
```

---

## 🎯 CORE FEATURES TO IMPLEMENT

### 1. **Dashboard Module**
- [ ] Key metrics cards (Today's Sales, Stock Value, Low Stock Items, Revenue)
- [ ] Sales chart (Daily/Weekly/Monthly)
- [ ] Inventory turnover chart
- [ ] Top selling products
- [ ] Recent transactions list
- [ ] Quick action buttons
- [ ] Alerts widget
- [ ] System notifications

### 2. **Inventory Management Module**
- [ ] Product listing with search/filter/sort
- [ ] Add/Edit/Delete products
- [ ] Bulk product import (CSV/Excel)
- [ ] Product categories management
- [ ] Stock level dashboard
- [ ] Low stock alerts (configurable threshold)
- [ ] Inventory history/audit trail
- [ ] Stock valuation report
- [ ] Unit conversion support
- [ ] Batch and serial number tracking
- [ ] Expiry date tracking and alerts
- [ ] Product images support

### 3. **Barcode Management Module**
- [ ] Barcode scanner integration (USB, Wireless)
- [ ] Barcode generation (EAN-13, Code128, QR)
- [ ] Batch barcode generation
- [ ] Barcode label printing
- [ ] Custom label templates
- [ ] SKU auto-generation
- [ ] Barcode validation
- [ ] Scanner configuration settings
- [ ] Scanner simulator for testing

### 4. **Stock In/Out Module**
- [ ] Stock receiving (GRN - Goods Receipt Note)
- [ ] Purchase order linking
- [ ] Stock issuance
- [ ] Inter-location transfers
- [ ] Stock adjustment (damage, loss, etc.)
- [ ] Stock return management
- [ ] Batch operations
- [ ] Movement history with reasons
- [ ] Transfer approval workflow (optional)

### 5. **Point of Sale (POS) Module**
- [ ] Fast product search and add to cart
- [ ] Barcode scanning during sale
- [ ] Shopping cart interface
- [ ] Quantity adjustment
- [ ] Discount management (percentage/fixed)
- [ ] Tax calculation
- [ ] Payment processing (Cash, Card, Check, Mobile)
- [ ] Invoice generation
- [ ] Receipt printing
- [ ] Change calculation
- [ ] Refund management
- [ ] Hold/Recall sales
- [ ] Customer lookup
- [ ] Quick customer creation

### 6. **Customer Management Module**
- [ ] Customer database
- [ ] Customer groups (Wholesale, Retail, VIP)
- [ ] Customer contact details
- [ ] Credit limit management
- [ ] Outstanding balance tracking
- [ ] Purchase history
- [ ] Loyalty points system
- [ ] Customer communication
- [ ] Bulk import/export

### 7. **Reporting Module**
- [ ] Sales reports (Daily, Weekly, Monthly, Custom date range)
- [ ] Inventory reports (Stock levels, Turnover, Valuation)
- [ ] Stock movement reports (In/Out history)
- [ ] Profit & Loss reports
- [ ] Customer reports (Top customers, Sales by customer)
- [ ] Supplier reports (Purchase history, outstanding payments)
- [ ] Low stock alerts
- [ ] Expiry date reports
- [ ] User activity reports
- [ ] Export to Excel/CSV/PDF
- [ ] Print reports
- [ ] Schedule and email reports
- [ ] Custom report builder
- [ ] Chart visualizations

### 8. **User Management Module**
- [ ] User registration/creation
- [ ] Role assignment (Admin, Manager, Staff, Viewer)
- [ ] Permission management
- [ ] User authentication
- [ ] Password management
- [ ] User activity tracking
- [ ] Session management
- [ ] Audit trail
- [ ] User dashboard preferences

### 9. **Settings Module**
- [ ] General settings (Company name, address, phone, email)
- [ ] Tax configuration
- [ ] Currency and localization
- [ ] Database backup/restore
- [ ] Theme preferences (Light/Dark mode)
- [ ] Printer configuration
- [ ] Scanner settings
- [ ] Email configuration
- [ ] API settings
- [ ] User preferences

### 10. **Supplier Management**
- [ ] Supplier database
- [ ] Supplier contact information
- [ ] Purchase order history
- [ ] Payment tracking
- [ ] Supplier performance metrics

### 11. **Backup & Recovery**
- [ ] Automatic backups
- [ ] Manual backup creation
- [ ] Database restoration
- [ ] Export data to JSON/XML
- [ ] Import data from backup

### 12. **Printing & Labeling**
- [ ] Invoice printing
- [ ] Receipt printing (thermal/standard)
- [ ] Barcode label printing
- [ ] Custom print templates
- [ ] Printer selection
- [ ] Print preview
- [ ] PDF export
- [ ] Print queue management

---

## 🎨 UI/UX SPECIFICATIONS

### Main Window Layout
```
┌─────────────────────────────────────────────────────┐
│ ☰  Stocki                          🔍  👤  ⚙️  🌙  │  ← Top Bar
├─────────────────────────────────────────────────────┤
│ ◆ Dashboard        │                                 │
│ ◆ Inventory        │                                 │
│ ◆ POS              │   Main Content Area              │
│ ◆ Customers        │                                 │
│ ◆ Reports          │                                 │
│ ◆ Stock In/Out     │                                 │
│ ◆ Users            │                                 │
│ ◆ Settings         │                                 │
│ ◆ Suppliers        │                                 │
│ ◆ Logout           │                                 │
├─────────────────────────────────────────────────────┤
│                      Status Bar                      │
└─────────────────────────────────────────────────────┘
```

### Color Scheme
- **Light Mode:**
  - Background: #FFFFFF, #F5F5F5
  - Text: #000000, #333333
  - Accent: #007AFF (Blue)
  - Borders: #E0E0E0

- **Dark Mode:**
  - Background: #1E1E1E, #2D2D2D
  - Text: #FFFFFF, #E0E0E0
  - Accent: #0084FF (Lighter Blue)
  - Borders: #404040

### Typography
- Headings: 18px, Bold
- Body Text: 13px, Regular
- Small Text: 11px, Regular
- Monospace (for codes): 12px, Monaco/Courier

### Components
- Rounded buttons with hover effects
- Toggle switches for options
- Data grids with sorting/filtering
- Combo boxes for dropdowns
- Modal dialogs for confirmations
- Toast notifications for feedback
- Progress bars for long operations

---

## 🔐 SECURITY & AUTHENTICATION

### Authentication
- Username + Password login
- Password hashing (bcrypt)
- Session management
- Timeout after inactivity
- Password change policy
- Login attempt limitation

### Authorization
- Role-Based Access Control (RBAC)
- Permission-based feature access
- Audit logging of all actions
- User activity tracking

### Data Protection
- SQL injection prevention (parameterized queries)
- No hardcoded sensitive data
- Encrypted connection strings
- Data validation on all inputs
- Principle of least privilege

---

## 🚀 IMPLEMENTATION ROADMAP

### Phase 1: Foundation (Week 1-2)
- [x] Project setup and architecture
- [ ] Database design and creation
- [ ] Base classes and interfaces
- [ ] Dependency injection setup
- [ ] Authentication system
- [ ] Logging system

### Phase 2: Core Modules (Week 3-6)
- [ ] Product management
- [ ] Inventory management
- [ ] Stock in/out
- [ ] Basic POS
- [ ] Basic reporting

### Phase 3: Advanced Features (Week 7-10)
- [ ] Barcode scanning/generation
- [ ] Advanced reporting
- [ ] Customer management
- [ ] Printing system
- [ ] User management

### Phase 4: Polish & Testing (Week 11-12)
- [ ] UI refinement
- [ ] Performance optimization
- [ ] Bug fixes
- [ ] Unit testing
- [ ] Integration testing
- [ ] Documentation

### Phase 5: Deployment (Week 13+)
- [ ] Production build
- [ ] Installation package
- [ ] User documentation
- [ ] Training materials

---

## 📦 REQUIRED NUGET PACKAGES

```xml
<!-- Database & ORM -->
<PackageReference Include="EntityFramework" Version="6.4.4" />
<PackageReference Include="System.Data.SQLite" Version="1.0.118" />

<!-- UI & Theming -->
<PackageReference Include="MahApps.Metro" Version="2.4.10" />
<PackageReference Include="ControlzEx" Version="4.4.0" />

<!-- Barcode -->
<PackageReference Include="ZXing.Net" Version="0.16.8" />
<PackageReference Include="BarcodeLib" Version="2.2.8" />

<!-- Reporting & Export -->
<PackageReference Include="iTextSharp" Version="5.5.13.3" />
<PackageReference Include="ClosedXML" Version="0.95.4" />
<PackageReference Include="EPPlus" Version="5.0.4" />

<!-- Printing -->
<PackageReference Include="EscPosNet" Version="3.0.0" />

<!-- Logging -->
<PackageReference Include="NLog" Version="4.15.0" />
<PackageReference Include="Serilog" Version="2.10.0" />

<!-- Dependency Injection -->
<PackageReference Include="Autofac" Version="6.4.0" />
<PackageReference Include="Microsoft.Extensions.DependencyInjection" Version="6.0.0" />

<!-- Data Validation -->
<PackageReference Include="FluentValidation" Version="10.4.0" />

<!-- JSON Serialization -->
<PackageReference Include="Newtonsoft.Json" Version="13.0.3" />

<!-- MVVM Framework -->
<PackageReference Include="Prism.Core" Version="8.1.97" />

<!-- Async/Threading -->
<PackageReference Include="AsyncFixer" Version="1.5.1" />
```

---

## 🧪 TESTING STRATEGY

### Unit Tests
- Service layer business logic
- Data validation
- Helper utilities
- Repository operations

### Integration Tests
- Database operations
- Service interactions
- Barcode generation

### UI Tests
- ViewModel logic
- Command execution
- Data binding

### Manual Tests
- POS workflow
- Barcode scanning simulation
- Printing functionality
- Report generation

---

## 📊 PERFORMANCE TARGETS

- Dashboard load: < 2 seconds
- Product search: < 500ms
- Report generation: < 5 seconds (depending on data)
- Barcode scanning: < 100ms response
- Database queries: < 1 second
- UI responsiveness: No freezing during operations

---

## 🎯 SUCCESS CRITERIA

1. ✅ All core modules fully functional
2. ✅ Barcode scanning/generation working
3. ✅ POS system operational
4. ✅ Reports generating correctly
5. ✅ macOS-inspired UI implemented
6. ✅ Database migrations working
7. ✅ User authentication secure
8. ✅ No critical bugs
9. ✅ Performance targets met
10. ✅ Documentation complete

---

## 📞 DEVELOPMENT NOTES

### Important Considerations
1. Use MVVM pattern for WPF
2. Implement proper error handling and logging
3. Use async/await for long operations
4. Validate all user inputs
5. Implement proper database transactions
6. Use dependency injection throughout
7. Write clean, maintainable code
8. Document complex business logic
9. Follow C# naming conventions
10. Optimize database queries

### Code Standards
- Follows Microsoft C# Coding Conventions
- XML documentation for public members
- Meaningful variable/method names
- Single Responsibility Principle
- DRY (Don't Repeat Yourself)
- SOLID principles

---

## 🔄 DEPLOYMENT

### System Requirements
- Windows 7 SP1 or later
- .NET Framework 4.8 installed
- 2GB RAM minimum
- 500MB disk space
- SQL Server 2016+ or SQLite

### Deployment Steps
1. Build in Release mode
2. Create installer (WIX or similar)
3. Include database setup script
4. Configuration wizard
5. Create backup of existing data
6. Test backup/restore

---

## 📝 DOCUMENTATION DELIVERABLES

1. **User Guide** - End-user documentation
2. **Developer Guide** - Technical documentation
3. **Database Schema** - ER diagrams and specs
4. **API Documentation** - If exposing APIs
5. **Deployment Guide** - Installation instructions
6. **Code Comments** - Inline documentation

---

## ✅ FINAL CHECKLIST

- [ ] All modules implemented
- [ ] Database schema created and tested
- [ ] UI designed and styled
- [ ] Authentication/Authorization working
- [ ] Barcode functionality operational
- [ ] POS system tested
- [ ] Reports generating correctly
- [ ] All CRUD operations working
- [ ] Error handling implemented
- [ ] Logging configured
- [ ] Unit tests written
- [ ] Integration tests passing
- [ ] UI tests passing
- [ ] Performance targets met
- [ ] Security audit completed
- [ ] Documentation complete
- [ ] Installation package created
- [ ] User training materials prepared
- [ ] Backup/Restore tested
- [ ] Production ready

---

## 🎉 PROJECT COMPLETION

Once all the above is implemented and tested, Stocki will be a fully functional, professional-grade stock management application ready for production use.

**Let's build the ultimate stock management app! 🚀**

---

*This specification document should be provided to the development team/AI to begin implementation.*
