# APJ Traders: Construction Materials Trading & Warehouse Management Platform

> **Project type:** Business management application for a construction
> raw-materials trading and distribution business\
> **Business name:** APJ Traders\
> **Initial market assumption:** India\
> **Document status:** Draft project requirements and technical
> blueprint\
> **Version:** 1.0

------------------------------------------------------------------------

## 1. Project Overview

APJ Traders will purchase construction materials from manufacturers,
distributors, quarries, brick kilns and other suppliers; receive and
store those materials in its warehouse or yard; and sell them to
contractors, builders, retailers and individual customers.

The application will manage the complete business lifecycle:

**Supplier → Purchase → Goods Receipt → Warehouse Inventory → Sales →
Dispatch/Delivery → Invoice → Payment**

The platform should provide a single, reliable view of purchasing, stock
availability, material movement, sales, customer balances, supplier
balances and business performance.

### 1.1 Business objectives

-   Maintain a central catalogue of construction materials, variants,
    grades and units of measurement.
-   Record supplier quotations, purchase orders, receipts, bills and
    payments.
-   Track inventory by warehouse, yard, storage area and (where useful)
    batch or lot.
-   Support materials that are measured and sold in different units,
    such as pieces, bags, kilograms, metric tonnes, cubic feet and cubic
    metres.
-   Prevent overselling and make available, reserved and damaged stock
    visible.
-   Create quotations, sales orders, invoices, delivery challans and
    dispatch records.
-   Support customer pickup and delivery to customer sites.
-   Track transport, loading, unloading, delivery charges and proof of
    delivery.
-   Track receivables, payables, expenses and cash/bank transactions.
-   Provide reports for stock, margins, sales, purchases, outstanding
    balances and operational performance.
-   Give owners and authorized staff access to business information from
    desktop and mobile devices.

### 1.2 Scope boundaries

The first release should focus on APJ Traders' own trading, inventory
and sales operations. It should not attempt to become a full
construction project-management, accounting, fleet telematics or
marketplace platform.

Integrations and advanced capabilities can be added after the core
business workflows are stable.

------------------------------------------------------------------------

## 2. Product Vision and Users

### 2.1 User types

  -----------------------------------------------------------------------
  User / role                         Main responsibilities
  ----------------------------------- -----------------------------------
  Business Owner / Administrator      Configuration, approvals, financial
                                      overview, users and reports

  Purchase Manager                    Suppliers, quotations, purchase
                                      orders and purchase returns

  Warehouse Manager                   Goods receipt, stock movement,
                                      stock counts and adjustments

  Sales Executive                     Customers, quotations, orders and
                                      follow-ups

  Billing / Accounts Staff            Invoices, receipts, supplier bills,
                                      payments and outstanding balances

  Dispatch Coordinator                Picking, loading, transport
                                      assignment and delivery status

  Delivery / Driver User              Assigned deliveries, status updates
                                      and proof of delivery

  Customer (future portal)            View quotations, orders, invoices
                                      and payment status
  -----------------------------------------------------------------------

Role-based access control must ensure that users can only access the
functions and records required for their work.

### 2.2 Primary user journeys

**Purchase and stock-in** 1. Staff selects a supplier and creates a
purchase order. 2. The order contains materials, specifications,
quantities, units, agreed rates, taxes and expected delivery date. 3.
Warehouse staff records the received quantity against the purchase
order. 4. Staff records shortages, excess, damage or rejected
quantities. 5. Accepted quantities are added to the appropriate
warehouse/yard stock. 6. The supplier bill and payment status are
recorded.

**Sales and stock-out** 1. Sales staff selects a customer and prepares a
quotation. 2. The application displays current available stock and the
applicable selling price. 3. The quotation is accepted and converted
into a sales order. 4. Stock is reserved, subject to the configured
reservation policy. 5. Warehouse staff picks and loads the material. 6.
Dispatch staff records vehicle, driver, delivery charges and
destination. 7. Delivery is confirmed and proof of delivery is captured.
8. An invoice is issued and payment/credit status is updated.

**Customer walk-in / counter sale** 1. Staff selects or creates a
customer. 2. Materials and quantities are added to a quick-sale screen.
3. The system checks stock and calculates taxes, discounts and totals.
4. Payment is recorded and the invoice/receipt is generated. 5. Stock is
reduced through the corresponding stock transaction.

------------------------------------------------------------------------

## 3. Functional Requirements

Priority definitions: **P0 = required for first usable release**, **P1 =
important next release**, **P2 = later enhancement**.

### 3.1 Dashboard and business overview

**P0** - Today's sales, purchases, collections and payments. - Current
stock summary and low-stock alerts. - Pending purchase receipts and
sales orders. - Deliveries pending, in transit and completed. - Customer
receivables and supplier payables. - Quick links to create a purchase
order, sales quotation, sales order and receipt.

**P1** - Sales and gross-margin trends. - Best-selling and slow-moving
materials. - Warehouse-wise stock value. - Sales by customer, product
category and salesperson. - Cash-flow and expense summaries.

Dashboard figures must be derived from transactional records, not
manually maintained totals.

### 3.2 Product and material catalogue

The catalogue must support categories, products, variants and
specifications.

Suggested initial categories:

  -----------------------------------------------------------------------
  Category                Example products /      Typical stock or sale
                          variants                units
  ----------------------- ----------------------- -----------------------
  Sand                    River sand, M-sand,     CFT, m³, tonne,
                          plastering sand,        truck/load
                          concrete sand           

  Bricks and blocks       Red clay bricks,        Piece, pallet, load
                          fly-ash bricks, solid   
                          blocks, hollow blocks,  
                          AAC blocks              

  Steel and reinforcement TMT bars, reinforcement kg, tonne, piece,
                          rods, binding wire,     bundle
                          steel bars              

  Stones and aggregates   6 mm, 10 mm, 20 mm, 40  CFT, m³, tonne, load
                          mm aggregate; jelly;    
                          crushed stone           

  Cement                  OPC, PPC, PSC and other Bag, kg, tonne
                          available grades/brands 
  -----------------------------------------------------------------------

The exact catalogue must be confirmed with APJ Traders before
configuration.

Each material should support: - SKU / internal product code and display
name. - Category, subcategory, brand and manufacturer. - Grade, size,
diameter, length, colour or other relevant specifications. - Purchase
unit, stock unit and sales unit. - Unit conversion rules, where
conversion is valid. - Default purchase and selling prices (with
effective dates or price lists). - Tax classification / HSN or
applicable tax code, configured with an accountant. - Minimum stock,
reorder level and preferred supplier. - Product image and attachments
(optional). - Active/inactive status.

**Important unit-of-measure rule:** Do not assume every unit is freely
interchangeable. For example, converting sand from cubic feet to tonnes
requires a material-specific density or an agreed operational conversion
factor. Store the conversion factor, its source, effective date and
approval. Do not use one generic conversion for all sand or aggregate.

### 3.3 Supplier management

**P0** - Supplier profile, contact details, addresses and GSTIN (where
applicable). - Supplier category and supplied materials. - Payment
terms, credit days and preferred transport details. - Supplier
quotations and negotiated rates. - Purchase order history. - Supplier
bills, debit notes, returns and outstanding balances. - Attachments such
as quotations, invoices and delivery documents.

### 3.4 Purchasing

**P0** - Purchase requisition (optional approval workflow). - Supplier
quotation comparison. - Purchase order with line items, quantity, unit,
rate, discount, tax and expected date. - Purchase order states: Draft,
Submitted, Partially Received, Received, Closed, Cancelled. - Partial
receipt against a purchase order. - Goods Receipt Note (GRN). - Record
accepted, rejected, damaged, short and excess quantities. - Record
freight, loading, unloading and other landed costs. - Supplier bill and
payment status. - Purchase return against a receipt or bill.

**P1** - Multi-level purchase approval based on amount or material
category. - Reorder suggestions based on minimum stock and recent
sales. - Supplier lead-time and price comparison reports.

### 3.5 Warehouse and inventory

Inventory accuracy is central to the business and should be designed
around a stock ledger.

**P0** - One or more warehouses / yards. - Storage areas, zones or bins
where required. - Stock receipt, issue, transfer, adjustment and
return. - Stock on hand, reserved stock and available stock. - Stock
ledger with a traceable record of every movement. - Physical stock count
and reconciliation. - Damaged, rejected, quarantined and saleable stock
statuses. - Low-stock and out-of-stock alerts. - Stock valuation using a
configured method (for example, weighted average); confirm the
accounting method with the accountant.

**P1** - Lot/batch tracking for selected materials. - QR/barcode labels
for packaged goods and warehouse locations. - Mobile stock count and
receiving screens. - Multiple yards and inter-warehouse transfer
approvals.

**Inventory invariants** - Never silently overwrite stock quantity. -
Every stock change must create a traceable stock transaction. - A posted
transaction should be reversed through a compensating transaction, not
deleted. - Prevent negative stock by default; any exception must require
explicit permission and an audit record. - Use database transactions and
concurrency controls when posting stock movements. - Keep physical
quantity and its unit explicit on every stock ledger entry.

### 3.6 Customer and CRM management

**P0** - Individual and business customer profiles. - Billing and
delivery addresses. - GSTIN and tax details, where applicable. - Contact
persons and communication details. - Customer-specific price lists and
discounts. - Credit limit and payment terms. - Quotation, order, invoice
and payment history. - Outstanding balance and ageing.

**P1** - Lead and enquiry tracking. - Follow-up reminders and notes. -
Customer segmentation and sales history. - WhatsApp/email notification
integration, subject to consent and provider setup.

### 3.7 Sales, billing and returns

**P0** - Sales quotation with validity date. - Sales order with delivery
or pickup option. - Availability check and stock reservation. - Partial
fulfilment and back-order handling. - Sales invoice with item-level
discounts, charges and taxes. - Delivery challan / dispatch document. -
Sales return, credit note and stock disposition. - Payment receipt and
allocation against one or more invoices. - Printable and downloadable
PDF documents.

**P1** - Counter-sale / POS-style billing. - Customer-specific price
contracts. - Sales commission and salesperson performance. - Online
customer enquiry or order portal.

### 3.8 Dispatch, transport and delivery

**P0** - Delivery address and site contact. - Delivery date/time window
and special instructions. - Vehicle number, vehicle type, driver and
contact number. - Transporter details and freight charge. - Loading and
dispatch confirmation. - Delivery status: Planned, Ready, Loaded,
Dispatched, In Transit, Delivered, Failed, Returned. - Proof of
delivery: receiver name, timestamp, notes and optional
photo/signature. - Delivery quantity and shortage/damage reporting.

**P1** - Vehicle capacity checks. - Trip and transporter cost reports. -
Route / location links. - Customer delivery notifications.

### 3.9 Finance and accounting operations

**P0** - Customer receipts and supplier payments. - Cash, bank, UPI and
other payment modes. - Invoice-level allocation and advance payments. -
Customer receivables and supplier payables. - Expense records (rent,
labour, loading, transport, utilities, etc.). - Credit/debit notes and
refund records. - Daily cash and bank summary. - Audit trail for
financial changes.

The first release may provide operational finance and outstanding
tracking. Full general-ledger accounting, bank reconciliation and
statutory reporting should either be integrated with a suitable
accounting product or implemented as a separately scoped accounting
module.

### 3.10 Reports and exports

**P0** - Current stock by material, unit and warehouse. - Stock movement
/ stock ledger. - Purchase register and supplier-wise purchases. - Sales
register and customer-wise sales. - Gross margin by product and period
(subject to complete cost allocation). - Low-stock and dead-stock
reports. - Customer outstanding and ageing. - Supplier outstanding and
ageing. - Delivery and pending-order reports. - Day-wise collection and
payment summary.

**P1** - Forecasted replenishment. - Material profitability after
freight and handling. - Salesperson performance. - Supplier lead-time
and quality performance. - Export to CSV/XLSX and scheduled report
delivery.

------------------------------------------------------------------------

## 4. Non-Functional Requirements

  -----------------------------------------------------------------------
  Area                                Requirement
  ----------------------------------- -----------------------------------
  Usability                           Simple, low-training workflows
                                      suitable for office, counter and
                                      warehouse staff

  Responsive UI                       Desktop, tablet and mobile browser
                                      support

  Performance                         Common screens should normally load
                                      within 2--3 seconds under expected
                                      operating load

  Reliability                         No lost or duplicated posted
                                      purchases, sales, payments or stock
                                      movements

  Security                            Authentication, role-based
                                      permissions, secure sessions and
                                      audit logs

  Data integrity                      Referential integrity,
                                      transactional posting and validated
                                      unit conversions

  Availability                        Initial target of 99.5% monthly
                                      availability, excluding agreed
                                      maintenance

  Scalability                         Start with one business and one
                                      warehouse; support additional
                                      warehouses and users without
                                      redesign

  Backup                              Automated database and file backups
                                      with documented restore tests

  Observability                       Centralized application logs, error
                                      tracking, health checks and
                                      infrastructure alerts

  Maintainability                     Automated tests, code review,
                                      documented APIs and repeatable
                                      deployments

  Localization                        INR currency, Indian address
                                      formats, configurable date/time and
                                      Asia/Kolkata timezone

  Compliance                          Tax and invoice configuration
                                      reviewed by a qualified Indian
                                      accounting professional
  -----------------------------------------------------------------------

Performance and availability targets are initial engineering targets and
should be validated against actual usage, hosting budget and business
criticality.

------------------------------------------------------------------------

## 5. Proposed Application Architecture

### 5.1 Recommended approach

Start with a **modular monolith** rather than microservices. This keeps
the first release easier to build, test, deploy and operate while
preserving clear module boundaries. Extract services only when scale,
team ownership or integration requirements justify the operational cost.

Suggested technology baseline, aligned to a Microsoft/.NET engineering
environment:

  -----------------------------------------------------------------------
  Layer                               Recommended technology
  ----------------------------------- -----------------------------------
  Backend API                         ASP.NET Core on .NET 10 LTS (or the
                                      latest supported LTS at
                                      implementation start)

  Frontend                            React + TypeScript, or Blazor if a
                                      single .NET-oriented stack is
                                      preferred

  Database                            PostgreSQL

  Cache / distributed coordination    Redis, introduced when justified

  Background jobs                     Hosted services initially; a
                                      durable job framework when required

  File storage                        Azure Blob Storage or S3-compatible
                                      object storage

  Authentication                      ASP.NET Core Identity / OpenID
                                      Connect provider

  API contract                        REST + OpenAPI / Swagger

  Containers                          Docker

  Hosting                             Azure App Service for Containers or
                                      Azure Container Apps

  CI/CD                               GitHub Actions or Azure DevOps

  Monitoring                          Azure Application Insights /
                                      OpenTelemetry

  Secrets                             Azure Key Vault or equivalent
                                      managed secrets service
  -----------------------------------------------------------------------

**Technology decision:** The URL supplied for APJ Traders is on a Frappe
Cloud domain. The public page redirected to the Frappe Cloud dashboard
and required JavaScript, so the existing site's application screens and
configuration could not be inspected. Before implementation, confirm
whether an ERPNext/Frappe site already exists and whether it contains
usable business data.

There are two sensible implementation paths:

1.  **Extend ERPNext/Frappe:** Prefer this if the current site is
    already an ERPNext implementation and its purchasing, stock, sales
    and accounting features meet most requirements. Customize doctypes,
    workflows, print formats and reports rather than rebuilding standard
    ERP functionality.
2.  **Build a custom .NET application:** Prefer this if APJ Traders
    needs tailored workflows, a custom user experience, or deeper
    control over the product roadmap. Integrate with ERPNext/accounting
    later if required.

Avoid building a custom accounting and inventory engine until the
existing Frappe/ERPNext setup has been assessed. The final technology
choice is an explicit discovery-phase decision.

### 5.2 Logical component view

``` text
Users
  ├── Owner / Admin
  ├── Purchase / Sales / Accounts
  └── Warehouse / Dispatch
          |
          v
Responsive Web Application
          |
          v
ASP.NET Core API
  ├── Identity & Access
  ├── Product Catalogue
  ├── Supplier & Customer
  ├── Purchasing & GRN
  ├── Inventory & Warehouse
  ├── Sales & Billing
  ├── Dispatch & Delivery
  ├── Payments & Expenses
  ├── Reports
  └── Audit & Notifications
          |
          +------ PostgreSQL
          +------ Redis (optional)
          +------ Object/File Storage
          +------ Background Job Worker
          +------ External Integrations
```

### 5.3 Suggested solution / repository structure

``` text
apj-traders/
├── README.md
├── docs/
│   ├── architecture/
│   ├── requirements/
│   ├── workflows/
│   ├── database/
│   ├── api/
│   ├── deployment/
│   └── decisions/
├── src/
│   ├── Api/
│   ├── Web/
│   ├── Application/
│   ├── Domain/
│   ├── Infrastructure/
│   ├── BackgroundJobs/
│   └── Shared/
├── tests/
│   ├── UnitTests/
│   ├── IntegrationTests/
│   └── EndToEndTests/
├── deploy/
│   ├── docker/
│   ├── azure/
│   └── scripts/
└── .github/
    └── workflows/
```

Keep business rules in the Domain/Application layers, persistence and
external integrations in Infrastructure, and HTTP concerns in the API
layer.

------------------------------------------------------------------------

## 6. Core Data Model

The following is a starting point for database design, not a final
normalized schema. Detailed entity relationships, indexes, constraints
and migration scripts should be produced during technical design.

### 6.1 Master data

-   `Company`
-   `User`, `Role`, `Permission`
-   `Warehouse`, `WarehouseLocation`
-   `ProductCategory`
-   `Product`
-   `ProductVariant` / `ProductSpecification`
-   `UnitOfMeasure`
-   `UnitConversion`
-   `PriceList`, `ProductPrice`
-   `Supplier`, `SupplierAddress`
-   `Customer`, `CustomerAddress`
-   `TaxCode`
-   `Vehicle`, `Transporter`, `Driver`

### 6.2 Purchasing and inventory

-   `PurchaseRequisition`
-   `PurchaseOrder`, `PurchaseOrderLine`
-   `GoodsReceipt`, `GoodsReceiptLine`
-   `SupplierBill`, `SupplierBillLine`
-   `PurchaseReturn`, `PurchaseReturnLine`
-   `StockLedgerEntry`
-   `StockReservation`
-   `StockTransfer`, `StockTransferLine`
-   `StockAdjustment`, `StockCount`
-   `InventoryBatch` (only where batch/lot tracking is needed)

### 6.3 Sales and delivery

-   `SalesQuotation`, `SalesQuotationLine`
-   `SalesOrder`, `SalesOrderLine`
-   `SalesInvoice`, `SalesInvoiceLine`
-   `SalesReturn`, `SalesReturnLine`
-   `Delivery`, `DeliveryLine`
-   `DeliveryTrip`
-   `PaymentReceipt`, `PaymentAllocation`
-   `SupplierPayment`
-   `Expense`
-   `CreditNote`, `DebitNote`
-   `Attachment`
-   `AuditLog`
-   `Notification`

### 6.4 Key data rules

-   Use immutable internal IDs (UUID or database-generated IDs) and
    human-readable document numbers.
-   Store money using fixed-precision decimal types, never
    floating-point types.
-   Store quantities using sufficient decimal precision and always store
    the unit.
-   Store timestamps in UTC and display them in the configured business
    timezone.
-   Store tax, discount and price values at the transaction line level
    so historical documents remain reproducible.
-   Preserve a snapshot of product description, unit, rate and tax
    details on posted documents.
-   Use explicit document states and posting timestamps.
-   Record who created, approved, posted, modified or reversed a
    transaction.
-   Use idempotency keys for retryable payment and integration
    endpoints.
-   Do not hard-delete posted financial or inventory transactions.

------------------------------------------------------------------------

## 7. API Requirements

Use versioned REST endpoints, request validation, consistent error
responses and OpenAPI documentation.

Example endpoint groups:

  ----------------------------------------------------------------------------
  Area                                Example endpoints
  ----------------------------------- ----------------------------------------
  Authentication                      `POST /api/v1/auth/login`,
                                      `POST /api/v1/auth/refresh`

  Products                            `GET /api/v1/products`,
                                      `POST /api/v1/products`

  Suppliers                           `GET /api/v1/suppliers`,
                                      `POST /api/v1/suppliers`

  Customers                           `GET /api/v1/customers`,
                                      `POST /api/v1/customers`

  Purchasing                          `POST /api/v1/purchase-orders`,
                                      `POST /api/v1/goods-receipts`

  Inventory                           `GET /api/v1/inventory/availability`,
                                      `GET /api/v1/inventory/ledger`

  Sales                               `POST /api/v1/quotations`,
                                      `POST /api/v1/sales-orders`

  Billing                             `POST /api/v1/sales-invoices`,
                                      `POST /api/v1/payments/receipts`

  Delivery                            `POST /api/v1/deliveries`,
                                      `PATCH /api/v1/deliveries/{id}/status`

  Reports                             `GET /api/v1/reports/stock`,
                                      `GET /api/v1/reports/sales`
  ----------------------------------------------------------------------------

These are illustrative contracts. Final request/response DTOs,
permissions, filters, pagination, validation rules and error codes must
be documented in `docs/api/`.

------------------------------------------------------------------------

## 8. Infrastructure and Environments

### 8.1 Environments

  -----------------------------------------------------------------------
  Environment             Purpose                 Data
  ----------------------- ----------------------- -----------------------
  Local                   Developer workstation   Synthetic / local test
                          and automated tests     data

  Development             Shared integration and  Synthetic data
                          feature testing         

  Staging / UAT           Business acceptance and Masked or synthetic
                          release verification    data

  Production              Live APJ Traders        Actual business data
                          operations              
  -----------------------------------------------------------------------

Production data must not be copied into development environments without
an approved masking process.

### 8.2 Initial cloud deployment

A practical initial Azure deployment could use:

-   Azure App Service (container-based) or Azure Container Apps for the
    API and web application.
-   Azure Database for PostgreSQL for managed relational storage.
-   Azure Blob Storage for invoice PDFs, supplier documents, delivery
    photos and attachments.
-   Azure Key Vault for connection strings, credentials, signing keys
    and integration secrets.
-   Azure Application Insights and Log Analytics for telemetry.
-   Azure Container Registry for versioned container images.
-   GitHub Actions or Azure DevOps for build, test and deployment.
-   Managed TLS certificates and HTTPS-only ingress.
-   Private networking and restricted database access where supported by
    the selected hosting plan.

Start with managed services and a modest production footprint. Size
compute, database storage and redundancy after measuring expected users,
transaction volume, attachment volume and business hours.

### 8.3 Logical infrastructure diagram

``` text
Browser / Mobile Browser
          |
       HTTPS
          |
   DNS + TLS / WAF
          |
   Web App / Frontend
          |
    API Application
       |       |
       |       +------ Background Worker
       |
       +------ Managed PostgreSQL
       +------ Object Storage
       +------ Key Vault
       +------ Monitoring / Logs
```

### 8.4 Network and security boundaries

-   Only the web/API ingress should be publicly reachable.
-   Database and cache should not be exposed directly to the internet.
-   Use managed identities where supported instead of long-lived
    credentials.
-   Separate production secrets from non-production secrets.
-   Restrict administrative access and require MFA for privileged
    accounts.
-   Apply least-privilege access to cloud resources.
-   Configure rate limiting and request-size limits.
-   Validate uploaded file type and size; scan files where supported.
-   Keep backups in a separate protected location/account where
    practical.

------------------------------------------------------------------------

## 9. Deployment Strategy

### 9.1 Containerization

Build reproducible Docker images for the web/API and background worker.
Pin base-image versions, run as a non-root user, keep secrets out of
images, and scan dependencies and images.

Illustrative local development services may include: - API and
frontend. - PostgreSQL. - Optional Redis. - Local object-storage
emulator or development storage configuration.

A `docker-compose.yml` can be added for local development once the
application skeleton exists.

### 9.2 CI/CD pipeline

Every pull request should run:

1.  Formatting and static analysis.
2.  Unit tests.
3.  Integration tests against a disposable database.
4.  Dependency and security checks.
5.  Frontend build and backend build.
6.  Container image build.
7.  Container vulnerability scan.

After merge to the release branch:

1.  Publish immutable, versioned images.
2.  Deploy to development.
3.  Run smoke tests and database migration checks.
4.  Promote the same image to staging.
5.  Complete user acceptance testing.
6.  Obtain production approval.
7.  Deploy to production using a controlled rollout.
8.  Run post-deployment health checks.

Database migrations must be backward-compatible where possible. Take a
verified backup before risky production migrations and document rollback
or forward-fix procedures.

### 9.3 Release and rollback

-   Use semantic versioning or a consistent release-numbering scheme.
-   Tag each release with a source commit and container image digest.
-   Maintain release notes and migration history.
-   Prefer rolling or blue/green deployment when supported by the
    hosting service.
-   Do not assume application rollback reverses database migrations.
-   Test recovery procedures in staging before relying on them in
    production.

------------------------------------------------------------------------

## 10. Security, Privacy and Audit

Minimum controls:

-   Secure password hashing or trusted identity-provider authentication.
-   MFA for owner and administrator accounts.
-   Role- and permission-based authorization on the server, not only in
    the UI.
-   HTTPS everywhere.
-   Input validation and parameterized database access.
-   Protection against common web vulnerabilities (OWASP Top 10).
-   Audit logs for changes to prices, stock, invoices, payments, credit
    limits and permissions.
-   Session expiration and secure refresh-token handling.
-   Encryption at rest and in transit using managed platform
    capabilities.
-   Secrets stored outside source control.
-   Rate limiting, lockout/throttling and suspicious-login monitoring.
-   Regular dependency updates and security reviews.
-   Defined retention and access policy for customer and supplier data.

Do not store card details. Use a payment gateway's hosted
checkout/tokenization flow if online payments are introduced.

------------------------------------------------------------------------

## 11. Indian Business and Tax Considerations

The application should be configurable for Indian business operations,
but tax and statutory rules must be validated by APJ Traders' accountant
or tax advisor before go-live.

Discovery items include:

-   GST registration status, GSTIN and place-of-supply rules.
-   HSN classification and applicable GST rates for each material.
-   Tax invoice, bill of supply, credit note and debit note formats as
    applicable.
-   E-invoicing applicability and integration requirements, if
    applicable to the business.
-   E-way bill applicability and generation/integration requirements, if
    applicable.
-   State-specific requirements and intra-state/inter-state transaction
    handling.
-   Cash, bank, UPI and other payment modes.
-   TDS or other deductions where relevant to the business.
-   Accounting method for inventory valuation and landed costs.

Do not hard-code tax rates or statutory thresholds. Make tax
configuration effective-dated and auditable, and verify current rules
before implementation and each compliance-related release.

------------------------------------------------------------------------

## 12. Testing and Quality Strategy

### 12.1 Essential test scenarios

**Purchasing** - Create, approve, partially receive and close a purchase
order. - Receive less or more than ordered. - Record damaged/rejected
quantities. - Prevent duplicate GRN posting. - Return material to a
supplier.

**Inventory** - Receive stock and verify ledger and balance. - Transfer
stock between locations. - Prevent unauthorized negative stock. -
Reconcile a physical count. - Verify unit conversions and rounding. -
Verify concurrent sales cannot oversell the same stock.

**Sales** - Create quotation and convert it to an order. - Reserve and
release stock. - Fulfil an order in multiple deliveries. - Cancel an
order and release its reservation. - Return sold goods and record their
disposition. - Verify discounts, taxes and totals.

**Finance** - Record full and partial payments. - Allocate one receipt
across multiple invoices. - Record an advance. - Reverse an incorrect
payment with an audit trail. - Verify customer and supplier ageing.

**Security** - Verify role boundaries and direct API authorization. -
Verify audit events. - Verify upload validation. - Verify secrets are
absent from logs and build artifacts.

### 12.2 Definition of Done

A feature is complete only when: - Acceptance criteria are met. -
Server-side validation and authorization are implemented. - Unit and
relevant integration tests pass. - Audit and error-handling requirements
are met. - API and user documentation are updated. - Responsive behavior
is checked on supported devices. - Logging and monitoring are sufficient
to diagnose failures. - The feature is deployed and verified in staging.

------------------------------------------------------------------------

## 13. Implementation Roadmap

A small team can deliver this incrementally. The time ranges below are
planning estimates, not commitments; actual duration depends on the
team, ERPNext reuse, data migration and statutory integration scope.

  ------------------------------------------------------------------------
  Phase                 Scope                          Indicative duration
  --------------------- --------------------- ----------------------------
  0\. Discovery         Confirm business                        1--2 weeks
                        process, existing     
                        Frappe setup,         
                        catalogue, units,     
                        taxes, users and      
                        reports               

  1\. Foundation        Repository,                             2--3 weeks
                        environments,         
                        authentication,       
                        roles, master data    
                        and audit             

  2\. Purchasing &      Suppliers, purchase                     3--5 weeks
  inventory             orders, GRN,          
                        warehouse, stock      
                        ledger and            
                        adjustments           

  3\. Sales & delivery  Customers,                              3--5 weeks
                        quotations, orders,   
                        invoices, dispatch    
                        and proof of delivery 

  4\. Finance & reports Receipts, payments,                     2--4 weeks
                        expenses, outstanding 
                        balances and core     
                        reports               

  5\. UAT & launch      Data migration, staff                   2--3 weeks
                        training, security    
                        checks, backups and   
                        production launch     
  ------------------------------------------------------------------------

### 13.1 MVP release recommendation

The first live release should include:

-   User login and role permissions.
-   Product catalogue with material specifications and units.
-   Supplier and customer management.
-   Purchase orders and goods receipt.
-   Warehouse stock ledger and stock availability.
-   Sales quotations, sales orders and invoices.
-   Delivery/dispatch records.
-   Payment receipts and outstanding balances.
-   Essential stock, sales, purchase and outstanding reports.
-   Audit trail, backup and restore procedure.

Defer advanced analytics, customer self-service, route optimization,
mobile apps, AI forecasting and complex multi-company features until the
MVP is in daily use.

### 13.2 Go-live acceptance criteria

-   APJ Traders' agreed material catalogue and opening stock are loaded
    and reconciled.
-   Supplier and customer masters are verified.
-   A purchase-to-stock and order-to-cash workflow passes UAT.
-   Unit conversion rules are approved and tested.
-   Invoice formats and tax configuration are approved by the
    accountant.
-   Users and permissions are verified.
-   Production backups and a restore test are completed.
-   Staff have received basic training.
-   Business owner signs off on the reports and operational workflow.

------------------------------------------------------------------------

## 14. Data Migration and Opening Balances

If APJ Traders is already operating, plan migration before development
is complete.

Potential source data: - Product/material lists and price lists. -
Supplier and customer records. - Opening stock by warehouse/location and
unit. - Outstanding customer invoices and balances. - Outstanding
supplier bills and balances. - Existing purchase and sales history, if
required.

Migration procedure: 1. Identify source files and data owners. 2. Agree
field mapping and duplicate-resolution rules. 3. Clean product names,
units, GSTINs and contact information. 4. Validate unit conversions. 5.
Import into a staging environment. 6. Reconcile stock quantities and
financial opening balances. 7. Obtain business-owner approval. 8. Freeze
source transactions during final cutover or define a controlled delta
import. 9. Import final data and verify totals before enabling live
transactions.

Keep an import log and retain the original source files securely.

------------------------------------------------------------------------

## 15. Operational Support and Disaster Recovery

Initial operational checklist:

-   Automated daily database backups and regular point-in-time recovery
    capability, according to the selected managed database plan.
-   Object-storage versioning or backup for important documents.
-   Defined backup retention (for example, daily and monthly retention
    tiers).
-   Quarterly restore test, at minimum, and after major infrastructure
    changes.
-   Application health checks and alerts for errors, latency, database
    capacity and failed jobs.
-   Centralized logs with sensitive information redacted.
-   Documented incident contacts and escalation steps.
-   Documented recovery objectives.

Set explicit **RPO** (maximum acceptable data loss) and **RTO** (maximum
acceptable recovery time) with the business owner. Suggested initial
discussion targets are RPO of 24 hours or better and RTO of 8 business
hours or better; tighten them if APJ Traders cannot tolerate that level
of interruption.

------------------------------------------------------------------------

## 16. Key Risks and Mitigations

  -----------------------------------------------------------------------
  Risk                                Mitigation
  ----------------------------------- -----------------------------------
  Incorrect sand/aggregate unit       Material-specific approved
  conversion                          conversion factors; show units on
                                      every document

  Stock mismatch between system and   GRN discipline, stock ledger,
  yard                                periodic counts and adjustment
                                      approvals

  Overselling                         Reservation logic, transactional
                                      stock posting and concurrency tests

  Unclear material                    Structured grades, sizes, brands
  quality/specification               and supplier/receipt notes

  Tax or invoice non-compliance       Accountant review, configurable tax
                                      rules and compliance validation

  Scope expansion                     MVP boundary, prioritized backlog
                                      and formal change control

  Staff adoption challenges           Simple screens, barcode/quick-entry
                                      options and hands-on training

  Existing Frappe data duplication    Discovery and data audit before
                                      selecting rebuild or integration

  Data loss or ransomware             Protected backups, restore drills,
                                      least privilege and MFA

  Vendor / hosting dependency         Infrastructure documentation,
                                      regular exports and tested recovery
                                      plan
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 17. Decisions Required from APJ Traders

These items should be resolved during discovery; they should not be
silently assumed by developers.

1.  Is the supplied Frappe Cloud site already configured with ERPNext,
    or is it only a newly created site?
2.  Should the project extend ERPNext/Frappe, or should it be a
    custom-built application?
3.  How many warehouses, yards and storage locations are required
    initially?
4.  Which materials, brands, grades, sizes and specifications will be
    sold at launch?
5.  Which units are used for purchase, storage and sale for each
    material?
6.  Who approves purchase orders, discounts, stock adjustments and
    credit sales?
7.  Are customers allowed to buy on credit? What are the credit limits
    and approval rules?
8.  Will APJ Traders deliver using its own vehicles, third-party
    transporters, or both?
9.  Is billing/accounting already handled by another system?
10. What GST, e-invoice and e-way bill requirements apply to the
    business?
11. How many users and concurrent users are expected in year one?
12. What is the initial and monthly hosting budget?
13. Is internet connectivity reliable at the warehouse/yard, or is
    offline capture required?
14. Which reports are essential to the owner for daily operations?

------------------------------------------------------------------------

## 18. Suggested Initial Backlog

### Epic A --- Foundation

-   [ ] Create repository and development conventions.
-   [ ] Configure local development environment.
-   [ ] Implement authentication and role-based authorization.
-   [ ] Implement audit logging.
-   [ ] Configure development, staging and production environments.

### Epic B --- Master Data

-   [ ] Product category and material catalogue.
-   [ ] Units of measure and controlled conversions.
-   [ ] Supplier management.
-   [ ] Customer management.
-   [ ] Warehouse and storage-location setup.
-   [ ] Price lists and tax configuration.

### Epic C --- Procurement and Inventory

-   [ ] Purchase order lifecycle.
-   [ ] Goods receipt and discrepancy capture.
-   [ ] Stock ledger and stock availability.
-   [ ] Stock transfer and adjustment.
-   [ ] Stock count and reconciliation.
-   [ ] Supplier bill and purchase return.

### Epic D --- Sales and Fulfilment

-   [ ] Sales quotation.
-   [ ] Sales order and reservation.
-   [ ] Invoice and document printing.
-   [ ] Delivery planning and dispatch.
-   [ ] Proof of delivery.
-   [ ] Sales return and credit note.

### Epic E --- Finance and Reporting

-   [ ] Payment receipts and allocations.
-   [ ] Supplier payments.
-   [ ] Expense capture.
-   [ ] Customer/supplier ageing.
-   [ ] Stock, purchase and sales reports.
-   [ ] Dashboard and alerts.

### Epic F --- Production Readiness

-   [ ] Automated CI/CD.
-   [ ] Monitoring and alerting.
-   [ ] Backup and restore test.
-   [ ] Security review.
-   [ ] UAT and staff training.
-   [ ] Production go-live checklist.

------------------------------------------------------------------------

## 19. Reference and Further Documentation

Create and maintain the following project documents as implementation
progresses:

-   `docs/requirements/business-processes.md` --- approved APJ Traders
    workflows.
-   `docs/requirements/product-catalogue.xlsx` --- material catalogue
    and unit rules.
-   `docs/architecture/architecture-decisions.md` --- technology and
    design decisions.
-   `docs/database/data-dictionary.md` --- entities, fields and
    constraints.
-   `docs/api/openapi.yaml` --- API contract.
-   `docs/deployment/environments.md` --- environment configuration and
    deployment procedure.
-   `docs/deployment/backup-restore.md` --- backup and recovery
    instructions.
-   `docs/operations/user-guide.md` --- operating instructions for APJ
    Traders staff.

## 20. Project Success Measures

The project should be evaluated against measurable business outcomes:

-   Every purchase receipt and sale is recorded in the system.
-   Stock on hand can be reconciled against physical stock.
-   Staff can identify available stock by material and warehouse.
-   Sales orders can be traced through dispatch and delivery.
-   Customer and supplier outstanding balances are visible.
-   The owner can review daily sales, collections, purchases and stock
    without manual spreadsheet consolidation.
-   Posted transactions have a reliable audit trail.
-   The application can be restored from backup within the agreed
    recovery objectives.

------------------------------------------------------------------------

**Document owner:** APJ Traders
