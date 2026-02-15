# Laravel eCommerce Platform
## Complete Technical Specification Document

**Version:** 1.1 (Launch-Ready Edition)  
**Date:** February 14, 2026  
**Development Timeline:** 55 Working Days  
**Status:** Ready for Development

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Technology Stack](#technology-stack)
3. [System Architecture](#system-architecture)
4. [Complete Feature List](#complete-feature-list)
5. [Database Schema](#database-schema)
6. [Module Specifications](#module-specifications)
7. [Security & Performance](#security-performance)
8. [Development Timeline](#development-timeline)
9. [Deployment & Infrastructure](#deployment-infrastructure)
10. [Testing Strategy](#testing-strategy)
11. [Support & Maintenance](#support-maintenance)

---

<div id="executive-summary"></div>

## 1. Executive Summary

### 1.1 Project Overview

This document outlines the complete technical specifications for a **modular, reusable eCommerce platform** built on Laravel 12. The platform is designed to be forked and customized for multiple clients while maintaining a clean, scalable architecture.

### 1.2 Key Objectives

- **Reusability:** Build once, deploy to multiple clients with minimal customization
- **Modularity:** Easy to add/remove features per client requirements
- **Scalability:** Handle growing product catalogs and order volumes
- **Security:** Industry-standard security practices and PCI compliance
- **Performance:** Fast page loads and optimized database queries
- **Professional:** Match or exceed industry standards (Daraz, Amazon)

### 1.3 Core Principles

| Principle | Implementation |
|-----------|----------------|
| **Config-Driven** | Client branding via .env files, no code changes |
| **Modular Architecture** | Separate modules for Catalog, Order, Payment, etc. |
| **No Niche Logic** | Generic database schema works for any product type |
| **Pluggable Gateways** | Easy to add payment methods |
| **SEO-First** | Clean URLs, meta tags, sitemaps built-in |

### 1.4 Delivery Timeline

- **Phase 1-4:** Base Product (40 days)
- **Phase 5:** Critical Features (15 days)
- **Total:** 55 working days
- **Status:** Launch-Ready eCommerce Platform

---

<div id="technology-stack"></div>

## 2. Technology Stack

### 2.1 Backend Technologies

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| **Framework** | Laravel | 12.x | Core application framework |
| **Language** | PHP | 8.3+ | Server-side programming |
| **Database** | MySQL | 8.0+ | Primary data storage |
| **Cache/Session** | Redis | 7.x | Caching, sessions, queues |
| **Search Engine** | Meilisearch | Latest | Fast product search |
| **Queue System** | Laravel Queue | - | Background job processing |
| **Task Scheduler** | Laravel Scheduler | - | Cron jobs, automated tasks |

### 2.2 Frontend Technologies

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| **Template Engine** | Blade | - | Server-side templating |
| **CSS Framework** | Tailwind CSS | 3.4+ | Utility-first styling |
| **JavaScript** | Alpine.js | 3.x | Lightweight interactivity |
| **Dynamic Components** | Livewire | 3.x | Reactive components |
| **Build Tool** | Vite | 5.x | Asset bundling |
| **Icons** | Heroicons | 2.x | UI icons |

### 2.3 Admin Panel

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| **Admin Framework** | Filament | 3.2+ | Complete admin panel |
| **Form Builder** | Filament Forms | 3.x | Dynamic form generation |
| **Table Builder** | Filament Tables | 3.x | Data tables with filters |
| **Dashboard** | Filament Widgets | 3.x | Analytics widgets |

### 2.4 Authentication & Authorization

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| **Authentication** | Laravel Fortify | 1.21+ | Headless auth backend |
| **Permissions** | Spatie Permission | 6.7+ | Role & permission management |
| **Session** | Laravel Session | - | User session handling |

### 2.5 File Management

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| **Media Library** | Spatie Media Library | 11.7+ | Image uploads & management |
| **Image Processing** | Intervention Image | 3.7+ | Image manipulation |
| **Storage** | Laravel Filesystem | - | File storage abstraction |

### 2.6 Utilities & Helpers

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| **Slugs** | Spatie Sluggable | 3.6+ | SEO-friendly URLs |
| **PDF Generation** | DomPDF | 3.0+ | Invoice & document PDFs |
| **HTTP Client** | Guzzle | 7.8+ | API requests |
| **Scout** | Laravel Scout | 10.10+ | Search indexing |

### 2.7 Development Tools

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| **Code Formatter** | Laravel Pint | 1.15+ | PSR-12 compliance |
| **Testing** | Pest PHP | 2.34+ | Feature & unit testing |
| **Package Manager** | Composer | 2.x | PHP dependencies |
| **Asset Manager** | NPM | 10.x | JavaScript dependencies |

### 2.8 Payment Gateway SDKs

| Gateway | Integration Method | Sandbox | Production |
|---------|-------------------|---------|-----------|
| **Cash on Delivery** | Built-in | ✅ | ✅ |
| **bKash** | REST API | ✅ | ✅ |
| **Nagad** | REST API | ✅ | ✅ |
| **SSLCommerz** | REST API | ✅ | Future |

### 2.9 Infrastructure Requirements

| Component | Minimum | Recommended | Purpose |
|-----------|---------|-------------|---------|
| **Web Server** | Nginx 1.18+ | Nginx 1.24+ | HTTP server |
| **PHP** | 8.3 | 8.3+ | Runtime |
| **MySQL** | 8.0 | 8.0+ | Database |
| **Redis** | 6.0 | 7.0+ | Cache/Session |
| **Memory** | 2GB RAM | 4GB+ RAM | Application |
| **Storage** | 20GB SSD | 50GB+ SSD | Files & DB |
| **SSL** | Let's Encrypt | Commercial | HTTPS |

### 2.10 Development Environment

```bash
# Recommended Local Setup
- OS: Ubuntu 22.04 LTS / macOS
- Docker: For consistent environments (optional)
- Laravel Herd: For local development (macOS)
- TablePlus / phpMyAdmin: Database management
- VS Code / PhpStorm: Code editor
```

---

<div id="system-architecture"></div>

## 3. System Architecture

### 3.1 Architectural Pattern

**Modular Monolith Architecture**

```
┌─────────────────────────────────────────────────────┐
│                  Laravel Application                 │
├─────────────────────────────────────────────────────┤
│                                                      │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐         │
│  │ Catalog  │  │  Order   │  │ Payment  │         │
│  │  Module  │  │  Module  │  │  Module  │         │
│  └──────────┘  └──────────┘  └──────────┘         │
│                                                      │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐         │
│  │ Customer │  │ Shipping │  │  Review  │         │
│  │  Module  │  │  Module  │  │  Module  │         │
│  └──────────┘  └──────────┘  └──────────┘         │
│                                                      │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐         │
│  │   Blog   │  │Analytics │  │   Core   │         │
│  │  Module  │  │  Module  │  │ Services │         │
│  └──────────┘  └──────────┘  └──────────┘         │
│                                                      │
├─────────────────────────────────────────────────────┤
│              Filament Admin Panel                    │
├─────────────────────────────────────────────────────┤
│         Laravel Core (Routing, ORM, Queue)          │
└─────────────────────────────────────────────────────┘
         │                    │                  │
         ▼                    ▼                  ▼
    MySQL 8.0+           Redis 7.x         Meilisearch
```

### 3.2 Directory Structure

```
app/
├── Core/                           # Shared utilities
│   ├── Contracts/                  # Interfaces
│   ├── Traits/                     # Reusable traits
│   ├── Helpers/                    # Helper functions
│   └── Services/                   # Shared services
│
├── Modules/                        # Business modules
│   ├── Catalog/                    # Products & Categories
│   │   ├── Models/
│   │   ├── Services/
│   │   ├── Repositories/
│   │   ├── Http/Controllers/
│   │   └── Filament/Resources/
│   │
│   ├── Order/                      # Cart, Checkout, Orders
│   │   ├── Models/
│   │   ├── Services/
│   │   ├── Enums/
│   │   └── Filament/Resources/
│   │
│   ├── Payment/                    # Payment gateways
│   │   ├── Contracts/
│   │   ├── Gateways/
│   │   ├── DTOs/
│   │   └── Services/
│   │
│   ├── Customer/                   # Customer management
│   ├── Shipping/                   # Shipping methods
│   ├── Review/                     # Product reviews
│   ├── Blog/                       # Content management
│   ├── Coupon/                     # Discount system
│   └── Analytics/                  # Visitor tracking
│
├── Filament/                       # Admin panel
│   ├── Resources/
│   ├── Pages/
│   └── Widgets/
│
└── Http/
    ├── Controllers/                # Frontend controllers
    ├── Middleware/                 # Custom middleware
    └── Requests/                   # Form requests

config/
├── client.php                      # Client customization
├── features.php                    # Feature flags
├── payment-gateways.php           # Payment config
└── shipping-methods.php           # Shipping config

resources/
├── views/
│   ├── layouts/
│   ├── components/
│   ├── pages/
│   └── emails/
└── css/

database/
├── migrations/
├── seeders/
└── factories/
```

### 3.3 Module Communication

```
Frontend Request
      ↓
Controller (HTTP Layer)
      ↓
Service (Business Logic)
      ↓
Repository (Data Access)
      ↓
Model (Eloquent ORM)
      ↓
Database
```

**Example Flow: Add to Cart**

```
1. User clicks "Add to Cart" → POST /cart/add
2. CartController receives request
3. Calls CartService->add($product, $quantity)
4. CartService validates stock availability
5. Updates session cart data
6. Returns response to controller
7. Controller redirects to cart page
8. Cart page displays updated items
```

### 3.4 Payment Gateway Architecture

```
┌─────────────────────────────────────────┐
│        PaymentGatewayInterface          │
│  (Contract defining all gateways)       │
└─────────────────────────────────────────┘
                    ▲
                    │ implements
        ┌───────────┼───────────┬───────────┐
        │           │           │           │
┌───────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐
│   COD     │ │  bKash  │ │  Nagad  │ │SSL Comm.│
│ Gateway   │ │ Gateway │ │ Gateway │ │ Gateway │
└───────────┘ └─────────┘ └─────────┘ └─────────┘
        │           │           │           │
        └───────────┴───────────┴───────────┘
                    │
            PaymentManager
         (Manages gateway selection)
```

### 3.5 Data Flow Diagram

```
┌──────────┐         ┌──────────┐         ┌──────────┐
│ Customer │────────▶│ Frontend │────────▶│  Cache   │
│ Browser  │◀────────│  (Blade) │◀────────│  (Redis) │
└──────────┘         └──────────┘         └──────────┘
                           │
                           ▼
                    ┌──────────┐
                    │Controller│
                    └──────────┘
                           │
                           ▼
                    ┌──────────┐         ┌──────────┐
                    │ Service  │────────▶│  Queue   │
                    │  Layer   │◀────────│  (Redis) │
                    └──────────┘         └──────────┘
                           │
                           ▼
                    ┌──────────┐
                    │  Model   │
                    │(Eloquent)│
                    └──────────┘
                           │
                           ▼
                    ┌──────────┐         ┌──────────┐
                    │  MySQL   │────────▶│Meilisearch│
                    │ Database │         │  Search   │
                    └──────────┘         └──────────┘
```

---

<div id="complete-feature-list"></div>

## 4. Complete Feature List

### 4.1 Core Features (Base Product)

#### 4.1.1 Product Catalog Management

| Feature | Description | Admin | Customer |
|---------|-------------|-------|----------|
| **Product CRUD** | Create, read, update, delete products | ✅ | ❌ |
| **Product Images** | Multiple images per product with zoom | ✅ | ✅ |
| **Image Gallery** | Sortable image gallery | ✅ | ✅ |
| **Categories** | Unlimited hierarchical categories | ✅ | ✅ |
| **Subcategories** | Multi-level category nesting | ✅ | ✅ |
| **Product Attributes** | Flexible key-value attributes | ✅ | ✅ |
| **SKU Management** | Unique product identifiers | ✅ | ✅ |
| **Stock Management** | Real-time inventory tracking | ✅ | ✅ |
| **Stock Status** | In stock, out of stock, backorder | ✅ | ✅ |
| **Low Stock Alerts** | Automated notifications | ✅ | ❌ |
| **Pricing** | Regular price, sale price, cost price | ✅ | ✅ |
| **Product Description** | Rich text descriptions | ✅ | ✅ |
| **Short Description** | Summary for listings | ✅ | ✅ |
| **SEO Meta Tags** | Title, description, keywords | ✅ | ❌ |
| **Product Slug** | SEO-friendly URLs | ✅ | ✅ |
| **Featured Products** | Highlight specific products | ✅ | ✅ |
| **Product Status** | Active/inactive toggle | ✅ | ❌ |
| **Bulk Actions** | Edit multiple products | ✅ | ❌ |

#### 4.1.2 Shopping Experience

| Feature | Description | Status |
|---------|-------------|--------|
| **Shopping Cart** | Session-based cart system | ✅ |
| **Add to Cart** | Quick add with AJAX | ✅ |
| **Cart Updates** | Change quantities, remove items | ✅ |
| **Cart Persistence** | Save cart across sessions | ✅ |
| **Guest Checkout** | Buy without registration | ✅ |
| **Registered Checkout** | Faster checkout for members | ✅ |
| **Multiple Addresses** | Save multiple shipping addresses | ✅ |
| **Address Book** | Manage saved addresses | ✅ |
| **Product Search** | Fast search with autocomplete | ✅ |
| **Advanced Filters** | Filter by price, brand, etc. | ✅ |
| **Product Sorting** | By price, name, date | ✅ |
| **Breadcrumbs** | Category navigation trail | ✅ |
| **Recently Viewed** | Track viewed products | ✅ |
| **Related Products** | Show similar items | ✅ |
| **Wishlist** | Save for later | ✅ |
| **Product Reviews** | Customer ratings & reviews | ✅ |
| **Review Moderation** | Admin approval required | ✅ |

#### 4.1.3 Order Management

| Feature | Description | Admin | Customer |
|---------|-------------|-------|----------|
| **Order Creation** | Process customer orders | ✅ | ✅ |
| **Order Listing** | View all orders | ✅ | ✅ |
| **Order Details** | Complete order information | ✅ | ✅ |
| **Order Status** | Pending, processing, completed, etc. | ✅ | ✅ |
| **Order Timeline** | Status change history | ✅ | ✅ |
| **Order Tracking** | Track by order number + email | ❌ | ✅ |
| **Order Cancellation** | Cancel pending orders | ✅ | ✅ |
| **Order Notes** | Customer and admin notes | ✅ | ✅ |
| **Invoice Generation** | PDF invoices | ✅ | ✅ |
| **Invoice Download** | Downloadable receipts | ✅ | ✅ |
| **Email Notifications** | Order confirmations & updates | ✅ | ✅ |
| **Order Search** | Search by number, customer | ✅ | ❌ |
| **Order Filters** | Filter by status, date | ✅ | ✅ |
| **Bulk Order Actions** | Process multiple orders | ✅ | ❌ |

#### 4.1.4 Payment Processing

| Feature | Description | Status |
|---------|-------------|--------|
| **Cash on Delivery** | Pay on delivery | ✅ |
| **bKash Integration** | Mobile banking (Bangladesh) | ✅ |
| **Nagad Integration** | Mobile banking (Bangladesh) | ✅ |
| **Payment Verification** | Automated verification | ✅ |
| **Transaction History** | Payment records | ✅ |
| **Refund Processing** | Issue refunds | ✅ |
| **Multiple Gateways** | Switch between methods | ✅ |
| **Gateway Selection** | Customer chooses at checkout | ✅ |
| **Secure Transactions** | SSL encryption | ✅ |
| **Payment Logs** | Detailed transaction logs | ✅ |

#### 4.1.5 Customer Management

| Feature | Description | Status |
|---------|-------------|--------|
| **Customer Registration** | Account creation | ✅ |
| **Login/Logout** | Secure authentication | ✅ |
| **Password Reset** | Email-based recovery | ✅ |
| **Profile Management** | Edit account details | ✅ |
| **Order History** | View past orders | ✅ |
| **Address Management** | Multiple addresses | ✅ |
| **Guest Accounts** | Track guest orders | ✅ |
| **Customer Dashboard** | Personal account page | ✅ |
| **Account Security** | Password hashing, 2FA ready | ✅ |

#### 4.1.6 Shipping & Delivery

| Feature | Description | Status |
|---------|-------------|--------|
| **Shipping Zones** | Different rates by location | ✅ |
| **Flat Rate Shipping** | Fixed shipping cost | ✅ |
| **Free Shipping** | Threshold-based | ✅ |
| **Shipping Calculator** | Show cost at checkout | ✅ |
| **Delivery Estimation** | Estimated delivery date | ✅ |
| **Tracking Numbers** | Courier tracking | ✅ |
| **Shipping Methods** | Multiple carrier options | ✅ |

#### 4.1.7 Marketing & Promotions

| Feature | Description | Status |
|---------|-------------|--------|
| **Coupon Codes** | Discount code system | ✅ |
| **Percentage Discounts** | % off products | ✅ |
| **Fixed Discounts** | Fixed amount off | ✅ |
| **Minimum Order Value** | Coupon requirements | ✅ |
| **Usage Limits** | Limit coupon uses | ✅ |
| **Expiry Dates** | Time-limited offers | ✅ |
| **Coupon Management** | Create, edit, deactivate | ✅ |
| **Newsletter Signup** | Email collection | ✅ |
| **Product Badges** | "New", "Sale" labels | ✅ |

#### 4.1.8 Content Management

| Feature | Description | Status |
|---------|-------------|--------|
| **Blog Posts** | Content marketing | ✅ |
| **Post Categories** | Organize content | ✅ |
| **Featured Images** | Post thumbnails | ✅ |
| **Rich Text Editor** | Formatted content | ✅ |
| **Post Status** | Draft, published, scheduled | ✅ |
| **SEO Optimization** | Meta tags for posts | ✅ |
| **Static Pages** | About, Contact, etc. | ✅ |
| **Legal Pages** | Terms, Privacy, Refund | ✅ |

#### 4.1.9 Analytics & Reporting

| Feature | Description | Status |
|---------|-------------|--------|
| **Visitor Tracking** | Page view analytics | ✅ |
| **Sales Dashboard** | Revenue charts | ✅ |
| **Top Products** | Best sellers report | ✅ |
| **Order Analytics** | Sales by period | ✅ |
| **Customer Analytics** | New vs returning | ✅ |
| **Traffic Sources** | Referrer tracking | ✅ |
| **Low Stock Report** | Inventory alerts | ✅ |

#### 4.1.10 Admin Panel Features

| Feature | Description | Status |
|---------|-------------|--------|
| **Dashboard** | Overview widgets | ✅ |
| **User Management** | Manage admin users | ✅ |
| **Role Management** | Custom roles & permissions | ✅ |
| **Permission System** | Granular access control | ✅ |
| **Activity Logs** | Admin action tracking | ✅ |
| **Settings Management** | Site configuration | ✅ |
| **Bulk Import** | CSV product import | ✅ |
| **Bulk Export** | Export data to CSV | ✅ |
| **Media Manager** | File upload management | ✅ |

#### 4.1.11 SEO Features

| Feature | Description | Status |
|---------|-------------|--------|
| **SEO-Friendly URLs** | Clean, readable URLs | ✅ |
| **Meta Tags** | Title, description, keywords | ✅ |
| **XML Sitemap** | Auto-generated sitemap | ✅ |
| **Robots.txt** | Search engine directives | ✅ |
| **Canonical URLs** | Duplicate content prevention | ✅ |
| **Schema Markup** | Structured data | ✅ |
| **Open Graph Tags** | Social media sharing | ✅ |
| **Image Alt Tags** | Accessibility & SEO | ✅ |
| **Page Speed Optimization** | Fast loading times | ✅ |

#### 4.1.12 Security Features

| Feature | Description | Status |
|---------|-------------|--------|
| **CSRF Protection** | Form security | ✅ |
| **XSS Protection** | Sanitized inputs | ✅ |
| **SQL Injection Prevention** | Parameterized queries | ✅ |
| **Password Hashing** | Bcrypt encryption | ✅ |
| **SSL/TLS Support** | HTTPS encryption | ✅ |
| **Rate Limiting** | Prevent abuse | ✅ |
| **Input Validation** | Server-side validation | ✅ |
| **File Upload Security** | Safe file handling | ✅ |
| **Session Security** | Secure session handling | ✅ |

### 4.2 Critical Features (Added in v1.1)

#### 4.2.1 Email Notification System

| Feature | Description | Recipients |
|---------|-------------|-----------|
| **Order Confirmation** | Sent when order placed | Customer |
| **Order Status Update** | Processing, shipped, delivered | Customer |
| **Payment Confirmation** | Payment received | Customer |
| **Admin Notification** | New order alert | Admin |
| **Low Stock Alert** | Stock below threshold | Admin |
| **Password Reset** | Forgot password email | Customer |
| **Welcome Email** | New registration | Customer |
| **Newsletter** | Marketing emails | Subscribers |

**Email Template Features:**
- Responsive HTML design
- Client branding (logo, colors)
- Order details table
- Tracking links
- Call-to-action buttons
- Footer with social links

#### 4.2.2 Guest Checkout Enhancement

| Feature | Description |
|---------|-------------|
| **Email Collection** | Required for order confirmation |
| **Phone Collection** | For delivery coordination |
| **Guest Order Tracking** | Track without account |
| **Post-Purchase Registration** | Convert to member |
| **Guest Order History** | View via email lookup |

#### 4.2.3 Order Tracking System

| Feature | Description |
|---------|-------------|
| **Track Order Page** | Dedicated tracking interface |
| **Order Number Lookup** | Search by order # |
| **Email Verification** | Security check |
| **Status Timeline** | Visual progress indicator |
| **Estimated Delivery** | Expected delivery date |
| **Courier Integration** | External tracking links |
| **Status Notifications** | Email on status change |

#### 4.2.4 PDF Invoice System

| Feature | Description |
|---------|-------------|
| **Invoice Generation** | Auto-generated PDFs |
| **Company Branding** | Logo, colors, details |
| **Order Details** | Complete itemization |
| **Tax Breakdown** | Transparent pricing |
| **Download Option** | Customer dashboard |
| **Email Attachment** | Sent with confirmation |
| **Print-Friendly** | Optimized layout |
| **Invoice Numbering** | Sequential tracking |

#### 4.2.5 Advanced Coupon System

| Feature | Description |
|---------|-------------|
| **Code Generator** | Unique codes |
| **Percentage Discount** | % off total |
| **Fixed Amount Discount** | ৳X off |
| **Minimum Purchase** | Order value requirement |
| **Maximum Discount** | Cap on percentage |
| **Usage Limits** | Per coupon |
| **Per-User Limits** | Per customer |
| **Date Ranges** | Start/end dates |
| **Product-Specific** | Specific products only |
| **Category-Specific** | Specific categories |
| **First Order Only** | New customer incentive |
| **Coupon Analytics** | Usage tracking |

#### 4.2.6 Shipping Cost Calculator

| Feature | Description |
|---------|-------------|
| **Zone-Based Rates** | Different areas |
| **Weight-Based** | By product weight |
| **Flat Rate** | Fixed cost |
| **Free Shipping** | Above threshold |
| **Real-Time Calculation** | Show before checkout |
| **Multiple Methods** | Standard, express |
| **Estimated Delivery** | Days to arrive |

### 4.3 Feature Comparison Matrix

| Feature Category | Features | Base (40d) | v1.1 (55d) |
|-----------------|----------|------------|------------|
| **Product Management** | 18 | ✅ | ✅ |
| **Shopping Experience** | 17 | ✅ | ✅ |
| **Order Management** | 14 | ✅ | ✅ |
| **Payment Processing** | 10 | ✅ | ✅ |
| **Customer Management** | 9 | ✅ | ✅ |
| **Shipping & Delivery** | 7 | ✅ | ✅ |
| **Marketing & Promotions** | 9 | ⚠️ Basic | ✅ Complete |
| **Email Notifications** | 8 | ❌ | ✅ |
| **Guest Checkout** | 5 | ❌ | ✅ |
| **Order Tracking** | 7 | ❌ | ✅ |
| **PDF Invoices** | 8 | ❌ | ✅ |
| **Shipping Calculator** | 7 | ❌ | ✅ |
| **Content Management** | 8 | ✅ | ✅ |
| **Analytics** | 7 | ✅ | ✅ |
| **Admin Panel** | 10 | ✅ | ✅ |
| **SEO Features** | 8 | ✅ | ✅ |
| **Security** | 9 | ✅ | ✅ |
| **TOTAL FEATURES** | **151** | **119** | **151** |

---

<div id="database-schema"></div>

## 5. Database Schema

### 5.1 Schema Overview

**Total Tables:** 25  
**Database Engine:** InnoDB  
**Character Set:** utf8mb4  
**Collation:** utf8mb4_unicode_ci

### 5.2 Complete Table Definitions

#### 5.2.1 Authentication Tables

**users**
```sql
CREATE TABLE `users` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `name` VARCHAR(255) NOT NULL,
  `email` VARCHAR(255) NOT NULL UNIQUE,
  `email_verified_at` TIMESTAMP NULL,
  `password` VARCHAR(255) NOT NULL,
  `phone` VARCHAR(20) NULL,
  `is_active` BOOLEAN DEFAULT TRUE,
  `remember_token` VARCHAR(100) NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  `deleted_at` TIMESTAMP NULL,
  
  INDEX idx_email (`email`),
  INDEX idx_phone (`phone`)
) ENGINE=InnoDB;
```

**password_reset_tokens**
```sql
CREATE TABLE `password_reset_tokens` (
  `email` VARCHAR(255) PRIMARY KEY,
  `token` VARCHAR(255) NOT NULL,
  `created_at` TIMESTAMP NULL
) ENGINE=InnoDB;
```

**sessions**
```sql
CREATE TABLE `sessions` (
  `id` VARCHAR(255) PRIMARY KEY,
  `user_id` BIGINT UNSIGNED NULL,
  `ip_address` VARCHAR(45) NULL,
  `user_agent` TEXT NULL,
  `payload` LONGTEXT NOT NULL,
  `last_activity` INT NOT NULL,
  
  INDEX idx_user (`user_id`),
  INDEX idx_activity (`last_activity`)
) ENGINE=InnoDB;
```

#### 5.2.2 Customer Tables

**customers**
```sql
CREATE TABLE `customers` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `user_id` BIGINT UNSIGNED NULL,
  `first_name` VARCHAR(100) NOT NULL,
  `last_name` VARCHAR(100) NOT NULL,
  `email` VARCHAR(255) NOT NULL UNIQUE,
  `phone` VARCHAR(20) NULL,
  `date_of_birth` DATE NULL,
  `gender` ENUM('male', 'female', 'other') NULL,
  `is_guest` BOOLEAN DEFAULT FALSE,
  `metadata` JSON NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  `deleted_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`user_id`) REFERENCES `users`(`id`) ON DELETE CASCADE,
  INDEX idx_email (`email`),
  INDEX idx_phone (`phone`),
  INDEX idx_guest (`is_guest`)
) ENGINE=InnoDB;
```

**addresses**
```sql
CREATE TABLE `addresses` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `customer_id` BIGINT UNSIGNED NOT NULL,
  `type` ENUM('billing', 'shipping') DEFAULT 'shipping',
  `full_name` VARCHAR(255) NOT NULL,
  `phone` VARCHAR(20) NOT NULL,
  `address_line_1` VARCHAR(255) NOT NULL,
  `address_line_2` VARCHAR(255) NULL,
  `city` VARCHAR(100) NOT NULL,
  `state` VARCHAR(100) NULL,
  `postal_code` VARCHAR(20) NULL,
  `country` VARCHAR(100) DEFAULT 'Bangladesh',
  `is_default` BOOLEAN DEFAULT FALSE,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`customer_id`) REFERENCES `customers`(`id`) ON DELETE CASCADE,
  INDEX idx_customer (`customer_id`),
  INDEX idx_customer_type (`customer_id`, `type`),
  INDEX idx_default (`is_default`)
) ENGINE=InnoDB;
```

#### 5.2.3 Catalog Tables

**categories**
```sql
CREATE TABLE `categories` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `parent_id` BIGINT UNSIGNED NULL,
  `name` VARCHAR(255) NOT NULL,
  `slug` VARCHAR(255) NOT NULL UNIQUE,
  `description` TEXT NULL,
  `image` VARCHAR(255) NULL,
  `icon` VARCHAR(100) NULL,
  `sort_order` INT DEFAULT 0,
  `is_active` BOOLEAN DEFAULT TRUE,
  `meta_title` VARCHAR(255) NULL,
  `meta_description` TEXT NULL,
  `meta_keywords` TEXT NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  `deleted_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`parent_id`) REFERENCES `categories`(`id`) ON DELETE CASCADE,
  INDEX idx_slug (`slug`),
  INDEX idx_parent (`parent_id`),
  INDEX idx_active (`is_active`),
  INDEX idx_sort (`sort_order`)
) ENGINE=InnoDB;
```

**products**
```sql
CREATE TABLE `products` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `sku` VARCHAR(100) NOT NULL UNIQUE,
  `name` VARCHAR(255) NOT NULL,
  `slug` VARCHAR(255) NOT NULL UNIQUE,
  `description` LONGTEXT NULL,
  `short_description` TEXT NULL,
  `price` DECIMAL(10,2) NOT NULL,
  `sale_price` DECIMAL(10,2) NULL,
  `cost_price` DECIMAL(10,2) NULL,
  `stock_quantity` INT DEFAULT 0,
  `stock_status` ENUM('in_stock', 'out_of_stock', 'backorder') DEFAULT 'in_stock',
  `low_stock_threshold` INT DEFAULT 5,
  `weight` VARCHAR(50) NULL,
  `dimensions` VARCHAR(100) NULL,
  `is_active` BOOLEAN DEFAULT TRUE,
  `is_featured` BOOLEAN DEFAULT FALSE,
  `sort_order` INT DEFAULT 0,
  `meta_title` VARCHAR(255) NULL,
  `meta_description` TEXT NULL,
  `meta_keywords` TEXT NULL,
  `metadata` JSON NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  `deleted_at` TIMESTAMP NULL,
  
  INDEX idx_sku (`sku`),
  INDEX idx_slug (`slug`),
  INDEX idx_active (`is_active`),
  INDEX idx_featured (`is_featured`),
  INDEX idx_price (`price`),
  INDEX idx_stock_status (`stock_status`)
) ENGINE=InnoDB;
```

**category_product** (Pivot)
```sql
CREATE TABLE `category_product` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `category_id` BIGINT UNSIGNED NOT NULL,
  `product_id` BIGINT UNSIGNED NOT NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`category_id`) REFERENCES `categories`(`id`) ON DELETE CASCADE,
  FOREIGN KEY (`product_id`) REFERENCES `products`(`id`) ON DELETE CASCADE,
  UNIQUE KEY unique_category_product (`category_id`, `product_id`),
  INDEX idx_category (`category_id`),
  INDEX idx_product (`product_id`)
) ENGINE=InnoDB;
```

**product_attributes**
```sql
CREATE TABLE `product_attributes` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `product_id` BIGINT UNSIGNED NOT NULL,
  `attribute_name` VARCHAR(100) NOT NULL,
  `attribute_value` VARCHAR(255) NOT NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`product_id`) REFERENCES `products`(`id`) ON DELETE CASCADE,
  INDEX idx_product (`product_id`),
  INDEX idx_name_value (`product_id`, `attribute_name`)
) ENGINE=InnoDB;
```

**product_images**
```sql
CREATE TABLE `product_images` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `product_id` BIGINT UNSIGNED NOT NULL,
  `path` VARCHAR(255) NOT NULL,
  `alt_text` VARCHAR(255) NULL,
  `sort_order` INT DEFAULT 0,
  `is_primary` BOOLEAN DEFAULT FALSE,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`product_id`) REFERENCES `products`(`id`) ON DELETE CASCADE,
  INDEX idx_product (`product_id`)
) ENGINE=InnoDB;
```

#### 5.2.4 Order Tables

**orders**
```sql
CREATE TABLE `orders` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `order_number` VARCHAR(50) NOT NULL UNIQUE,
  `customer_id` BIGINT UNSIGNED NOT NULL,
  `status` VARCHAR(50) DEFAULT 'pending',
  `payment_status` VARCHAR(50) DEFAULT 'pending',
  `payment_method` VARCHAR(50) NULL,
  `transaction_id` VARCHAR(255) NULL,
  `shipping_method` VARCHAR(100) NULL,
  `subtotal` DECIMAL(10,2) DEFAULT 0,
  `tax` DECIMAL(10,2) DEFAULT 0,
  `shipping_cost` DECIMAL(10,2) DEFAULT 0,
  `discount` DECIMAL(10,2) DEFAULT 0,
  `total` DECIMAL(10,2) DEFAULT 0,
  `shipping_address` JSON NULL,
  `billing_address` JSON NULL,
  `customer_notes` TEXT NULL,
  `admin_notes` TEXT NULL,
  `tracking_number` VARCHAR(100) NULL,
  `shipped_at` TIMESTAMP NULL,
  `delivered_at` TIMESTAMP NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  `deleted_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`customer_id`) REFERENCES `customers`(`id`) ON DELETE CASCADE,
  INDEX idx_order_number (`order_number`),
  INDEX idx_customer (`customer_id`),
  INDEX idx_status (`status`),
  INDEX idx_payment_status (`payment_status`),
  INDEX idx_created (`created_at`)
) ENGINE=InnoDB;
```

**order_items**
```sql
CREATE TABLE `order_items` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `order_id` BIGINT UNSIGNED NOT NULL,
  `product_id` BIGINT UNSIGNED NULL,
  `product_sku` VARCHAR(100) NOT NULL,
  `product_name` VARCHAR(255) NOT NULL,
  `product_description` TEXT NULL,
  `product_attributes` JSON NULL,
  `price` DECIMAL(10,2) NOT NULL,
  `quantity` INT NOT NULL,
  `subtotal` DECIMAL(10,2) NOT NULL,
  `tax` DECIMAL(10,2) DEFAULT 0,
  `discount` DECIMAL(10,2) DEFAULT 0,
  `total` DECIMAL(10,2) NOT NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`order_id`) REFERENCES `orders`(`id`) ON DELETE CASCADE,
  FOREIGN KEY (`product_id`) REFERENCES `products`(`id`) ON DELETE SET NULL,
  INDEX idx_order (`order_id`),
  INDEX idx_product (`product_id`)
) ENGINE=InnoDB;
```

#### 5.2.5 Payment Tables

**transactions**
```sql
CREATE TABLE `transactions` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `order_id` BIGINT UNSIGNED NOT NULL,
  `transaction_id` VARCHAR(255) NOT NULL UNIQUE,
  `gateway` VARCHAR(50) NOT NULL,
  `status` VARCHAR(50) NOT NULL,
  `amount` DECIMAL(10,2) NOT NULL,
  `currency` VARCHAR(3) DEFAULT 'BDT',
  `gateway_response` JSON NULL,
  `notes` TEXT NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`order_id`) REFERENCES `orders`(`id`) ON DELETE CASCADE,
  INDEX idx_order (`order_id`),
  INDEX idx_transaction (`transaction_id`),
  INDEX idx_status (`status`)
) ENGINE=InnoDB;
```

#### 5.2.6 Coupon Tables

**coupons**
```sql
CREATE TABLE `coupons` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `code` VARCHAR(50) NOT NULL UNIQUE,
  `type` ENUM('percentage', 'fixed') NOT NULL,
  `value` DECIMAL(10,2) NOT NULL,
  `minimum_order_value` DECIMAL(10,2) NULL,
  `maximum_discount` DECIMAL(10,2) NULL,
  `usage_limit` INT NULL,
  `per_user_limit` INT NULL,
  `used_count` INT DEFAULT 0,
  `starts_at` TIMESTAMP NULL,
  `expires_at` TIMESTAMP NULL,
  `is_active` BOOLEAN DEFAULT TRUE,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  INDEX idx_code (`code`),
  INDEX idx_active (`is_active`),
  INDEX idx_dates (`starts_at`, `expires_at`)
) ENGINE=InnoDB;
```

**coupon_usage**
```sql
CREATE TABLE `coupon_usage` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `coupon_id` BIGINT UNSIGNED NOT NULL,
  `order_id` BIGINT UNSIGNED NOT NULL,
  `customer_id` BIGINT UNSIGNED NOT NULL,
  `discount_amount` DECIMAL(10,2) NOT NULL,
  `created_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`coupon_id`) REFERENCES `coupons`(`id`) ON DELETE CASCADE,
  FOREIGN KEY (`order_id`) REFERENCES `orders`(`id`) ON DELETE CASCADE,
  FOREIGN KEY (`customer_id`) REFERENCES `customers`(`id`) ON DELETE CASCADE,
  INDEX idx_coupon (`coupon_id`),
  INDEX idx_customer (`customer_id`)
) ENGINE=InnoDB;
```

#### 5.2.7 Review Tables

**product_reviews**
```sql
CREATE TABLE `product_reviews` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `product_id` BIGINT UNSIGNED NOT NULL,
  `customer_id` BIGINT UNSIGNED NOT NULL,
  `order_id` BIGINT UNSIGNED NULL,
  `rating` TINYINT NOT NULL CHECK (`rating` >= 1 AND `rating` <= 5),
  `title` VARCHAR(255) NULL,
  `comment` TEXT NOT NULL,
  `is_verified_purchase` BOOLEAN DEFAULT FALSE,
  `is_approved` BOOLEAN DEFAULT FALSE,
  `approved_at` TIMESTAMP NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`product_id`) REFERENCES `products`(`id`) ON DELETE CASCADE,
  FOREIGN KEY (`customer_id`) REFERENCES `customers`(`id`) ON DELETE CASCADE,
  FOREIGN KEY (`order_id`) REFERENCES `orders`(`id`) ON DELETE SET NULL,
  INDEX idx_product (`product_id`),
  INDEX idx_customer (`customer_id`),
  INDEX idx_approved (`product_id`, `is_approved`)
) ENGINE=InnoDB;
```

#### 5.2.8 Wishlist Tables

**wishlists**
```sql
CREATE TABLE `wishlists` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `customer_id` BIGINT UNSIGNED NOT NULL,
  `product_id` BIGINT UNSIGNED NOT NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`customer_id`) REFERENCES `customers`(`id`) ON DELETE CASCADE,
  FOREIGN KEY (`product_id`) REFERENCES `products`(`id`) ON DELETE CASCADE,
  UNIQUE KEY unique_wishlist (`customer_id`, `product_id`),
  INDEX idx_customer (`customer_id`)
) ENGINE=InnoDB;
```

#### 5.2.9 Blog Tables

**post_categories**
```sql
CREATE TABLE `post_categories` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `name` VARCHAR(255) NOT NULL,
  `slug` VARCHAR(255) NOT NULL UNIQUE,
  `description` TEXT NULL,
  `is_active` BOOLEAN DEFAULT TRUE,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  INDEX idx_slug (`slug`)
) ENGINE=InnoDB;
```

**posts**
```sql
CREATE TABLE `posts` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `post_category_id` BIGINT UNSIGNED NULL,
  `author_id` BIGINT UNSIGNED NOT NULL,
  `title` VARCHAR(255) NOT NULL,
  `slug` VARCHAR(255) NOT NULL UNIQUE,
  `excerpt` TEXT NULL,
  `content` LONGTEXT NOT NULL,
  `featured_image` VARCHAR(255) NULL,
  `status` ENUM('draft', 'published', 'scheduled') DEFAULT 'draft',
  `published_at` TIMESTAMP NULL,
  `views_count` INT DEFAULT 0,
  `meta_title` VARCHAR(255) NULL,
  `meta_description` TEXT NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  `deleted_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`post_category_id`) REFERENCES `post_categories`(`id`) ON DELETE SET NULL,
  FOREIGN KEY (`author_id`) REFERENCES `users`(`id`) ON DELETE CASCADE,
  INDEX idx_slug (`slug`),
  INDEX idx_status (`status`),
  INDEX idx_published (`published_at`)
) ENGINE=InnoDB;
```

#### 5.2.10 Analytics Tables

**visitors**
```sql
CREATE TABLE `visitors` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `ip_address` VARCHAR(45) NOT NULL,
  `user_agent` VARCHAR(500) NULL,
  `referer` VARCHAR(500) NULL,
  `device_type` VARCHAR(50) NULL,
  `browser` VARCHAR(100) NULL,
  `platform` VARCHAR(100) NULL,
  `country` VARCHAR(100) NULL,
  `city` VARCHAR(100) NULL,
  `visited_url` VARCHAR(500) NOT NULL,
  `customer_id` BIGINT UNSIGNED NULL,
  `visited_at` TIMESTAMP NOT NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`customer_id`) REFERENCES `customers`(`id`) ON DELETE SET NULL,
  INDEX idx_ip (`ip_address`),
  INDEX idx_visited_at (`visited_at`),
  INDEX idx_customer (`customer_id`)
) ENGINE=InnoDB;
```

#### 5.2.11 Stock Notification Tables

**stock_notifications**
```sql
CREATE TABLE `stock_notifications` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `product_id` BIGINT UNSIGNED NOT NULL,
  `email` VARCHAR(255) NOT NULL,
  `phone` VARCHAR(20) NULL,
  `notified` BOOLEAN DEFAULT FALSE,
  `notified_at` TIMESTAMP NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  FOREIGN KEY (`product_id`) REFERENCES `products`(`id`) ON DELETE CASCADE,
  INDEX idx_product (`product_id`),
  INDEX idx_notified (`notified`)
) ENGINE=InnoDB;
```

#### 5.2.12 Newsletter Tables

**newsletter_subscribers**
```sql
CREATE TABLE `newsletter_subscribers` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `email` VARCHAR(255) NOT NULL UNIQUE,
  `is_active` BOOLEAN DEFAULT TRUE,
  `subscribed_at` TIMESTAMP NULL,
  `unsubscribed_at` TIMESTAMP NULL,
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  INDEX idx_email (`email`),
  INDEX idx_active (`is_active`)
) ENGINE=InnoDB;
```

#### 5.2.13 Settings Tables

**settings**
```sql
CREATE TABLE `settings` (
  `id` BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  `key` VARCHAR(255) NOT NULL UNIQUE,
  `value` TEXT NULL,
  `type` VARCHAR(50) DEFAULT 'string',
  `group` VARCHAR(100) DEFAULT 'general',
  `created_at` TIMESTAMP NULL,
  `updated_at` TIMESTAMP NULL,
  
  INDEX idx_key (`key`),
  INDEX idx_group (`group`)
) ENGINE=InnoDB;
```

#### 5.2.14 Spatie Permission Tables

These are created by running: `php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"`

- `roles`
- `permissions`
- `model_has_permissions`
- `model_has_roles`
- `role_has_permissions`

#### 5.2.15 Spatie Media Library Tables

Created by running: `php artisan vendor:publish --provider="Spatie\MediaLibrary\MediaLibraryServiceProvider" --tag="migrations"`

- `media`

### 5.3 Entity Relationship Diagram

```
┌──────────┐         ┌───────────┐         ┌──────────┐
│  USERS   │────1:1──│ CUSTOMERS │────1:N──│ADDRESSES │
└──────────┘         └───────────┘         └──────────┘
                            │
                            │ 1:N
                            ▼
                     ┌───────────┐         ┌──────────────┐
                     │  ORDERS   │────1:N──│ ORDER_ITEMS  │
                     └───────────┘         └──────────────┘
                            │                      │
                            │ 1:N                  │ N:1
                            ▼                      ▼
                     ┌─────────────┐       ┌──────────┐
                     │TRANSACTIONS │       │ PRODUCTS │
                     └─────────────┘       └──────────┘
                                                  │
                ┌─────────────────────────────────┼──────────────────┐
                │                                 │                  │
                │ N:M                             │ 1:N              │ 1:N
                ▼                                 ▼                  ▼
         ┌────────────┐                   ┌─────────────┐    ┌──────────────┐
         │ CATEGORIES │                   │  ATTRIBUTES │    │PRODUCT_IMAGES│
         └────────────┘                   └─────────────┘    └──────────────┘
                │                                 
                │ self-reference (parent_id)      
                ▼                                 
         ┌────────────┐                   
         │ CATEGORIES │ (subcategories)   
         └────────────┘                   
```

### 5.4 Index Strategy

**Critical Indexes for Performance:**

```sql
-- Products
CREATE INDEX idx_products_search ON products(name, sku, description(100));
CREATE INDEX idx_products_active_price ON products(is_active, price);
CREATE INDEX idx_products_featured_active ON products(is_featured, is_active);

-- Orders
CREATE INDEX idx_orders_customer_status ON orders(customer_id, status);
CREATE INDEX idx_orders_date_range ON orders(created_at, status);

-- Category Performance
CREATE INDEX idx_category_active_sort ON categories(is_active, sort_order);

-- Full-text Search (optional, if not using Meilisearch)
ALTER TABLE products ADD FULLTEXT INDEX ft_products(name, description);
```

### 5.5 Database Size Estimates

**Projected Storage (1 Year):**

| Table | Est. Rows | Size/Row | Total Size |
|-------|-----------|----------|------------|
| Products | 5,000 | 5 KB | ~25 MB |
| Categories | 200 | 2 KB | ~400 KB |
| Orders | 50,000 | 3 KB | ~150 MB |
| Order Items | 150,000 | 1 KB | ~150 MB |
| Customers | 30,000 | 2 KB | ~60 MB |
| Product Images | 20,000 | 500 B | ~10 MB |
| Visitors | 1,000,000 | 500 B | ~500 MB |
| **TOTAL** | | | **~900 MB** |

*Note: Actual file storage for images not included (typically 5-50 GB)*

---

## 6. Module Specifications

*(Continued in next section due to length...)*

### 6.1 Catalog Module

**Responsibilities:**
- Product management (CRUD)
- Category hierarchy
- Product attributes
- Image management
- Search & filtering
- Stock tracking

**Key Classes:**
```
Models:
- Product
- Category
- ProductAttribute
- ProductImage

Services:
- ProductService
- CategoryService
- SearchService

Repositories:
- ProductRepository
- CategoryRepository

Controllers:
- ProductController (Frontend)
- CategoryController (Frontend)

Filament Resources:
- ProductResource
- CategoryResource
```

### 6.2 Order Module

**Responsibilities:**
- Shopping cart
- Checkout process
- Order creation
- Order management
- Invoice generation
- Order tracking

**Key Classes:**
```
Models:
- Order
- OrderItem
- Cart (Session-based)

Services:
- CartService
- CheckoutService
- OrderService
- InvoiceService

Enums:
- OrderStatus
- PaymentStatus

Controllers:
- CartController
- CheckoutController
- OrderController

Filament Resources:
- OrderResource
```

### 6.3 Payment Module

**Responsibilities:**
- Gateway abstraction
- Payment processing
- Transaction logging
- Refund handling

**Key Classes:**
```
Contracts:
- PaymentGatewayInterface

Gateways:
- CashOnDelivery
- BkashGateway
- NagadGateway

DTOs:
- PaymentRequest
- PaymentResponse

Services:
- PaymentManager

Models:
- Transaction
```

### 6.4 Customer Module

**Responsibilities:**
- Customer accounts
- Profile management
- Address management
- Order history

**Key Classes:**
```
Models:
- Customer
- Address

Services:
- CustomerService

Controllers:
- CustomerController
- ProfileController

Filament Resources:
- CustomerResource
```

### 6.5 Coupon Module

**Responsibilities:**
- Coupon creation
- Validation
- Application
- Usage tracking

**Key Classes:**
```
Models:
- Coupon
- CouponUsage

Services:
- CouponService

Filament Resources:
- CouponResource
```

### 6.6 Shipping Module

**Responsibilities:**
- Shipping method management
- Cost calculation
- Zone-based rates

**Key Classes:**
```
Contracts:
- ShippingMethodInterface

Methods:
- FlatRateShipping
- FreeShipping
- ZoneBasedShipping

Services:
- ShippingManager
```

### 6.7 Email Module

**Responsibilities:**
- Email notifications
- Template management
- Queue management

**Key Classes:**
```
Mails:
- OrderConfirmationMail
- OrderStatusUpdateMail
- WelcomeMail
- PasswordResetMail

Jobs:
- SendOrderConfirmationJob
- SendLowStockAlertJob
```

---

<div id="security-performance"></div>

## 7. Security & Performance

### 7.1 Security Measures

**Authentication & Authorization:**
- ✅ Laravel Fortify for authentication
- ✅ Spatie Permission for role-based access
- ✅ Bcrypt password hashing
- ✅ Session security with HTTP-only cookies
- ✅ CSRF token protection
- ✅ Rate limiting on login attempts

**Input Validation:**
- ✅ Server-side form validation
- ✅ XSS protection (Blade auto-escaping)
- ✅ SQL injection prevention (Eloquent ORM)
- ✅ File upload validation (type, size, extension)

**Data Protection:**
- ✅ SSL/TLS encryption in transit
- ✅ Database encryption at rest (optional)
- ✅ Sensitive data hashing
- ✅ GDPR compliance ready

**Payment Security:**
- ✅ PCI-DSS compliant gateway integrations
- ✅ No card data stored locally
- ✅ Secure API communication
- ✅ Transaction logging

### 7.2 Performance Optimization

**Database Optimization:**
```php
// Query optimization
Product::with(['categories', 'attributes', 'images'])
    ->active()
    ->paginate(24);

// Database indexes on frequently queried columns
// Eager loading to prevent N+1 queries
```

**Caching Strategy:**
```php
// Cache category tree (rarely changes)
Cache::remember('categories.tree', 86400, fn() => 
    Category::with('children')->roots()->get()
);

// Cache featured products
Cache::remember('products.featured', 3600, fn() => 
    Product::featured()->active()->limit(10)->get()
);
```

**Asset Optimization:**
- CSS/JS minification with Vite
- Image optimization (WebP format)
- Lazy loading for images
- CDN integration support

**Server Optimization:**
- OPcache enabled
- Redis for sessions/cache
- Queue workers for background jobs
- Response compression (gzip)

**Performance Targets:**
- Homepage load: < 2 seconds
- Product page: < 1 second
- Search results: < 500ms
- Lighthouse score: > 90

---

<div id="development-timeline"></div>

## 8. Development Timeline

### 8.1 Complete 55-Day Breakdown

**PHASE 1: Foundation (Days 1-10)**

| Day | Task | Deliverable |
|-----|------|-------------|
| 1-2 | Project setup, Laravel 11 installation, environment config | Working dev environment |
| 3-5 | Database design, create all migrations | Database schema ready |
| 6-7 | Seed roles, permissions, test data | Sample data populated |
| 8-9 | Authentication setup (Fortify) | Login/register working |
| 10 | Testing & bug fixes | Clean foundation |

**PHASE 2: Core Models & Business Logic (Days 11-25)**

| Day | Task | Deliverable |
|-----|------|-------------|
| 11-13 | Product module (models, services, repository) | Product CRUD backend |
| 14-15 | Category module with hierarchy | Category management |
| 16-17 | Product attributes & images | Flexible product system |
| 18-20 | Cart service implementation | Shopping cart working |
| 21-22 | Checkout service & validation | Checkout logic complete |
| 23-25 | Order service & processing | Order system functional |

**PHASE 3: Payment Integration (Days 26-30)**

| Day | Task | Deliverable |
|-----|------|-------------|
| 26-27 | Payment gateway architecture | Interface & manager |
| 28 | Cash on Delivery implementation | COD working |
| 29 | bKash gateway integration | bKash payments |
| 30 | Nagad gateway integration | Nagad payments |

**PHASE 4: Admin Panel (Days 31-38)**

| Day | Task | Deliverable |
|-----|------|-------------|
| 31-32 | Filament setup, Product resource | Product admin |
| 33 | Category resource | Category admin |
| 34-35 | Order resource with filters | Order management |
| 36 | Customer resource | Customer admin |
| 37 | Review & blog resources | Content moderation |
| 38 | Dashboard widgets & analytics | Admin dashboard |

**PHASE 5: Frontend (Days 39-46)**

| Day | Task | Deliverable |
|-----|------|-------------|
| 39-40 | Layout, navigation, homepage | Site structure |
| 41 | Product listing page with filters | Browse products |
| 42 | Product detail page | Product view |
| 43 | Cart & checkout pages | Purchase flow |
| 44 | Customer dashboard | Account pages |
| 45 | Static pages (about, contact, etc.) | Info pages |
| 46 | Mobile responsiveness | Mobile-optimized |

**PHASE 6: Critical Features (Days 47-55)**

| Day | Task | Deliverable |
|-----|------|-------------|
| 47-48 | Email notification system | Order emails |
| 49 | Guest checkout implementation | No-login purchase |
| 50 | Order tracking page | Track orders |
| 51 | PDF invoice generation | Downloadable invoices |
| 52-53 | Coupon system (backend + admin) | Discount codes |
| 54 | Shipping cost calculator | Dynamic shipping |
| 55 | Final testing & polish | Production ready |

**PHASE 7: Deployment Prep (Days 56-58 - Optional)**

| Day | Task | Deliverable |
|-----|------|-------------|
| 56 | Performance optimization | Fast loading |
| 57 | SEO optimization (meta tags, sitemap) | Search engine ready |
| 58 | Final client review & fixes | Approved for launch |

### 8.2 Milestone Payment Schedule

| Milestone | Day | Payment | Deliverable |
|-----------|-----|---------|-------------|
| **Milestone 1** | Day 10 | 20% | Foundation complete |
| **Milestone 2** | Day 25 | 25% | Core logic working |
| **Milestone 3** | Day 38 | 25% | Admin panel done |
| **Milestone 4** | Day 46 | 20% | Frontend complete |
| **Milestone 5** | Day 55 | 10% | All features integrated |

---

<div id="deployment-infrastructure"></div>

## 9. Deployment & Infrastructure

### 9.1 Recommended Hosting

**Option A: Managed Laravel Hosting**
- Laravel Forge + DigitalOcean/AWS
- Automated deployments
- Zero-downtime deployments
- Built-in SSL management

**Option B: Shared/VPS Hosting**
- cPanel with CloudLinux
- SSH access required
- Manual deployment
- Cost-effective for starting

### 9.2 Server Requirements

```
Minimum Specifications:
- CPU: 2 cores
- RAM: 4GB
- Storage: 50GB SSD
- Bandwidth: Unmetered
- PHP: 8.3+
- MySQL: 8.0+
- Redis: 7.x
- SSL Certificate

Recommended Specifications:
- CPU: 4 cores
- RAM: 8GB
- Storage: 100GB SSD
- CDN: CloudFlare
- Backup: Daily automated
```

### 9.3 Environment Configuration

```bash
# Production .env example
APP_ENV=production
APP_DEBUG=false
APP_URL=https://client-store.com

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_DATABASE=ecommerce_db
DB_USERNAME=db_user
DB_PASSWORD=secure_password

CACHE_DRIVER=redis
SESSION_DRIVER=redis
QUEUE_CONNECTION=redis

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

# Payment Gateways
PAYMENT_BKASH_ENABLED=true
BKASH_APP_KEY=your_key
BKASH_APP_SECRET=your_secret
BKASH_SANDBOX=false

# Email
MAIL_MAILER=smtp
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=noreply@client-store.com
MAIL_PASSWORD=email_password
MAIL_FROM_ADDRESS=noreply@client-store.com
```

### 9.4 Deployment Checklist

**Pre-Launch:**
- [ ] All migrations run successfully
- [ ] Database seeded with sample data
- [ ] Email configuration tested
- [ ] Payment gateways tested (sandbox)
- [ ] SSL certificate installed
- [ ] Backup system configured
- [ ] Performance optimization done
- [ ] Security audit completed

**Launch Day:**
- [ ] Switch to production environment
- [ ] Enable production payment gateways
- [ ] Configure DNS settings
- [ ] Set up monitoring (UptimeRobot)
- [ ] Enable error logging (Sentry)
- [ ] Test all critical user flows
- [ ] Monitor server resources

**Post-Launch:**
- [ ] Daily database backups
- [ ] Weekly security updates
- [ ] Monthly performance review
- [ ] Quarterly feature updates

---

<div id="testing-strategy"></div>

## 10. Testing Strategy

### 10.1 Testing Types

**Unit Tests:**
```php
test('product price calculation with sale price', function () {
    $product = Product::factory()->create([
        'price' => 1000,
        'sale_price' => 800,
    ]);
    
    expect($product->effective_price)->toBe(800.0);
    expect($product->is_on_sale)->toBeTrue();
    expect($product->discount_percentage)->toBe(20);
});
```

**Feature Tests:**
```php
test('user can complete checkout', function () {
    $product = Product::factory()->create(['price' => 500]);
    $user = User::factory()->create();
    
    $this->actingAs($user)
        ->post('/cart/add', ['product_id' => $product->id])
        ->assertRedirect('/cart');
        
    $this->post('/checkout', [
        'shipping_address' => [...],
        'payment_method' => 'cod',
    ])->assertRedirect('/orders');
    
    $this->assertDatabaseHas('orders', [
        'customer_id' => $user->customer->id,
        'status' => 'pending',
    ]);
});
```

**Browser Tests (Dusk):**
```php
test('guest can search and purchase product', function () {
    Browser::drive(function (Browser $browser) {
        $browser->visit('/')
            ->type('@search', 'laptop')
            ->press('@search-button')
            ->assertSee('Search Results')
            ->click('@first-product')
            ->press('@add-to-cart')
            ->click('@checkout')
            ->type('@email', 'test@example.com')
            ->press('@place-order')
            ->assertSee('Order Confirmed');
    });
});
```

### 10.2 Test Coverage Goals

| Module | Coverage Target |
|--------|----------------|
| Product Service | 90%+ |
| Cart Service | 90%+ |
| Order Service | 95%+ |
| Payment Gateways | 85%+ |
| Controllers | 70%+ |

---

<div id="support-maintenance"></div>

## 11. Support & Maintenance

### 11.1 Included Support (First Year)

**Technical Support:**
- Bug fixes for reported issues
- Security patch updates
- Laravel framework updates
- Database optimization
- Performance monitoring

**Scope:**
- Response time: 24-48 hours
- Critical bugs: 4-8 hours
- Monthly health check
- Quarterly security audit

**Exclusions:**
- New feature development
- Custom integrations
- Third-party plugin issues
- Server management
- Content updates

### 11.2 Maintenance Schedule

**Daily:**
- Automated database backups
- Log file monitoring
- Error alert notifications

**Weekly:**
- Security scan
- Performance metrics review
- Broken link check

**Monthly:**
- Dependency updates
- Database optimization
- Cache clearing
- Review analytics

**Quarterly:**
- Security audit
- Performance optimization
- Feature usage analysis
- Technology stack updates

### 11.3 SLA (Service Level Agreement)

| Issue Severity | Response Time | Resolution Time |
|---------------|---------------|-----------------|
| **Critical** (Site down) | 2 hours | 8 hours |
| **High** (Payment failure) | 4 hours | 24 hours |
| **Medium** (Feature bug) | 24 hours | 72 hours |
| **Low** (UI issue) | 48 hours | 1 week |

### 11.4 Contact & Support Channels

**Technical Issues:**
- Email: dev-support@your-company.com
- Ticketing System: support.your-company.com
- Emergency Hotline: +880-XXX-XXXXXX

**Business Hours:**
- Monday-Friday: 9:00 AM - 6:00 PM (Bangladesh Time)
- Emergency Support: 24/7 for critical issues

---

## 12. Appendices

### 12.1 Glossary

| Term | Definition |
|------|------------|
| **SKU** | Stock Keeping Unit - Unique product identifier |
| **Eloquent ORM** | Laravel's database abstraction layer |
| **Blade** | Laravel's templating engine |
| **Filament** | Admin panel framework for Laravel |
| **Redis** | In-memory data structure store for caching |
| **Meilisearch** | Fast, open-source search engine |
| **COD** | Cash on Delivery payment method |
| **SSL/TLS** | Secure Sockets Layer / Transport Layer Security |
| **CSRF** | Cross-Site Request Forgery protection |
| **XSS** | Cross-Site Scripting protection |
| **PCI-DSS** | Payment Card Industry Data Security Standard |

### 12.2 Reference Links

**Official Documentation:**
- Laravel 11: https://laravel.com/docs/11.x
- Filament 3: https://filamentphp.com/docs/3.x
- Tailwind CSS 3: https://tailwindcss.com/docs
- Livewire 3: https://livewire.laravel.com/docs/3.x

**Package Documentation:**
- Spatie Permission: https://spatie.be/docs/laravel-permission
- Spatie Media Library: https://spatie.be/docs/laravel-medialibrary
- Laravel Scout: https://laravel.com/docs/11.x/scout
- DomPDF: https://github.com/barryvdh/laravel-dompdf

**Payment Gateways:**
- bKash Developer: https://developer.bka.sh
- Nagad Developer: https://developer.nagad.com.bd

### 12.3 Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Feb 2026 | Initial base product specification |
| 1.1 | Feb 2026 | Added critical features (email, guest checkout, etc.) |

---

## Document Approval

**Prepared By:**  
Development Team  
[Your Company Name]

**Date:** February 14, 2026

**Approved By:**  
_______________________  
Client Name / Signature

**Date:** _______________

---

**END OF DOCUMENT**

*This is a living document and will be updated as the project evolves. All stakeholders will be notified of significant changes.*
