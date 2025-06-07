This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Folder Sturcture 
```
ecommerce-app/
├── app/                               # Next.js App Router
│   ├── (admin)/                      # Admin routes group
│   │   ├── layout.tsx                # Admin layout with sidebar (shadcn/ui)
│   │   ├── dashboard/                # Admin dashboard
│   │   │   └── page.tsx              # Dashboard with analytics (Acertinity UI charts)
│   │   ├── users/                    # User management
│   │   │   ├── page.tsx              # Users list (shadcn/ui DataTable)
│   │   │   └── [userId]/             # Single user view/edit
│   │   │       └── page.tsx
│   │   ├── products/                 # Product management
│   │   │   ├── page.tsx              # Products list (shadcn/ui DataTable)
│   │   │   ├── new/                  # Create new product
│   │   │   │   └── page.tsx         # Form with Zod validation
│   │   │   └── [productId]/          # Edit product
│   │   │       └── page.tsx         # Form with Zod validation
│   │   ├── orders/                   # Order management
│   │   │   ├── page.tsx              # Orders list (shadcn/ui DataTable)
│   │   │   └── [orderId]/            # Single order details
│   │   │       └── page.tsx
│   │   ├── content/                  # Content management
│   │   │   ├── pages/                # Manage static pages
│   │   │   │   └── page.tsx         # WYSIWYG editor (Acertinity UI)
│   │   │   ├── banners/              # Manage banners
│   │   │   │   └── page.tsx
│   │   │   └── promotions/           # Manage promotions
│   │   │       └── page.tsx
│   │   ├── funds/                    # Financial management
│   │   │   ├── transactions/         # Transaction history
│   │   │   │   └── page.tsx
│   │   │   ├── withdrawals/          # Withdrawal requests
│   │   │   │   └── page.tsx
│   │   │   └── reports/              # Financial reports
│   │   │       └── page.tsx         # Acertinity UI charts
│   │   ├── notifications/            # Admin notifications
│   │   │   ├── page.tsx              # Notifications list (shadcn/ui)
│   │   │   └── [notificationId]/     # Notification details
│   │   │       └── page.tsx
│   ├── (auth)/                       # Authentication routes
│   │   ├── layout.tsx                # Auth layout (minimal, shadcn/ui)
│   │   ├── login/                    # Login page
│   │   │   ├── page.tsx              # Login form with Zod
│   │   │   └── otp-verification/     # OTP verification
│   │   │       └── page.tsx         # OTP input (Acertinity UI)
│   │   └── register/                 # Registration page
│   │       ├── page.tsx              # Registration form with Zod
│   │       └── otp-verification/     # OTP verification
│   │           └── page.tsx
│   ├── (main)/                       # Customer-facing routes
│   │   ├── layout.tsx                # Main layout with header/footer (shadcn/ui)
│   │   ├── page.tsx                  # Home page (Acertinity UI hero)
│   │   ├── account/                  # User account section
│   │   │   ├── profile/              # Profile management
│   │   │   │   └── page.tsx         # Form with Zod
│   │   │   ├── addresses/            # Address book
│   │   │   │   └── page.tsx         # Leaflet map integration
│   │   │   └── orders/               # User orders
│   │   │       └── [orderId]/        # Single order view
│   │   │           └── page.tsx
│   │   ├── cart/                     # Shopping cart
│   │   │   └── page.tsx              # Cart with shadcn/ui components
│   │   ├── checkout/                 # Checkout process
│   │   │   ├── address/              # Address selection
│   │   │   │   └── page.tsx         # Leaflet map, Zod validation
│   │   │   ├── payment/              # Payment method selection
│   │   │   │   └── page.tsx         # Payment tokenization
│   │   │   └── confirmation/         # Order confirmation
│   │   │       └── page.tsx
│   │   ├── products/                 # Product catalog
│   │   │   ├── page.tsx              # All products (shadcn/ui grid)
│   │   │   └── [category]/           # Category view
│   │   │       └── [productId]/      # Single product view
│   │   │           └── page.tsx     # Acertinity UI product showcase
│   │   ├── track-order/              # Order tracking
│   │   │   └── [orderId]/            # Track specific order
│   │   │       └── page.tsx
│   │   ├── notifications/            # User notifications
│   │   │   ├── page.tsx              # Notifications list (shadcn/ui)
│   │   │   └── [notificationId]/     # Notification details
│   │   │       └── page.tsx
│   ├── api/                          # API routes (Next.js)
│   │   ├── admin/                    # Admin API endpoints
│   │   │   ├── dashboard/            # Dashboard data
│   │   │   │   └── route.ts         # GET, Redis cached
│   │   │   ├── users/                # User management
│   │   │   │   └── route.ts         # GET, POST, PUT, DELETE (JWT)
│   │   │   ├── products/             # Product management
│   │   │   │   └── route.ts         # GET, POST, PUT, DELETE (JWT)
│   │   │   ├── orders/               # Order management
│   │   │   │   └── route.ts         # GET, PUT (JWT)
│   │   │   ├── content/              # Content management
│   │   │   │   └── route.ts         # GET, POST, PUT (JWT)
│   │   │   ├── funds/                # Fund management
│   │   │   │   └── route.ts         # GET, POST (JWT)
│   │   │   └── notifications/        # Admin notifications
│   │   │       ├── route.ts          # GET, POST (JWT)
│   │   │       └── [id]/             # Single notification
│   │   │           └── route.ts     # GET, PUT, DELETE (JWT)
│   │   ├── auth/                     # Authentication APIs
│   │   │   ├── login/                # Login endpoint
│   │   │   │   └── route.ts         # POST, CSRF protection
│   │   │   ├── register/             # Registration endpoint
│   │   │   │   └── route.ts         # POST, CSRF protection
│   │   │   └── verify-otp/           # OTP verification
│   │   │       └── route.ts         # POST, CSRF protection
│   │   ├── cart/                     # Cart operations
│   │   │   └── route.ts             # GET, POST, PUT, DELETE (JWT)
│   │   ├── checkout/                 # Checkout operations
│   │   │   └── route.ts             # POST, payment tokenization
│   │   ├── orders/                   # Order operations
│   │   │   └── route.ts             # GET, POST (JWT)
│   │   ├── products/                 # Product data
│   │   │   └── route.ts             # GET, Redis cached
│   │   ├── user/                     # User data
│   │   │   └── route.ts             # GET, PUT (JWT)
│   │   └── notifications/            # User notifications
│   │       ├── route.ts              # GET, POST (JWT)
│   │       └── [id]/                 # Single notification
│   │           └── route.ts         # GET, PUT, DELETE (JWT)
│   ├── layout.tsx                    # Root layout (shadcn/ui)
│   └── page.tsx                      # Root home page (redirect to (main))
├── components/                       # Reusable components
│   ├── admin/                        # Admin components
│   │   ├── DashboardCards.tsx        # Summary cards (Acertinity UI)
│   │   ├── AnalyticsCharts.tsx       # Charts (Acertinity UI)
│   │   ├── UserTable.tsx             # User table (shadcn/ui DataTable)
│   │   ├── ProductForm.tsx           # Product form (shadcn/ui, Zod)
│   │   ├── OrderDetails.tsx          # Order details (shadcn/ui)
│   │   ├── ContentEditor.tsx         # WYSIWYG editor (Acertinity UI)
│   │   ├── FundReports.tsx           # Financial reports (Acertinity UI)
│   │   └── AdminNotificationAlert.tsx # Admin alerts (shadcn/ui)
│   ├── auth/                         # Auth components
│   │   ├── LoginForm.tsx             # Login form (shadcn/ui, Zod)
│   │   ├── RegisterForm.tsx          # Registration form (shadcn/ui, Zod)
│   │   └── OTPInput.tsx              # OTP input (Acertinity UI)
│   ├── cart/                         # Cart components
│   │   ├── CartItem.tsx              # Cart item (shadcn/ui)
│   │   └── CartSummary.tsx           # Cart summary (shadcn/ui)
│   ├── checkout/                     # Checkout components
│   │   ├── AddressForm.tsx           # Address form (shadcn/ui, Leaflet)
│   │   ├── PaymentMethods.tsx        # Payment selection (shadcn/ui)
│   │   └── OrderSummary.tsx          # Order summary (shadcn/ui)
│   ├── products/                     # Product components
│   │   ├── ProductCard.tsx           # Product card (Acertinity UI)
│   │   ├── ProductDetails.tsx        # Product details (Acertinity UI)
│   │   └── ProductVariations.tsx     # Product variants (shadcn/ui)
│   ├── notifications/                # Notification components
│   │   ├── NotificationBell.tsx      # Notification icon (shadcn/ui)
│   │   ├── NotificationList.tsx      # Notification dropdown (shadcn/ui)
│   │   ├── NotificationItem.tsx      # Single notification (shadcn/ui)
│   ├── ui/                           # General UI components
│   │   ├── Header.tsx                # Site header (shadcn/ui)
│   │   ├── Footer.tsx                # Site footer (shadcn/ui)
│   │   ├── Navbar.tsx                # Navigation bar (shadcn/ui)
│   │   └── RatingStars.tsx           # Rating stars (Acertinity UI)
│   └── shared/                       # Shared components
│       ├── AddressSelector.tsx       # Address picker (Leaflet map)
│       ├── Button.tsx                # Reusable button (shadcn/ui)
│       └── Card.tsx                  # Reusable card (shadcn/ui)
├── config/                           # Configuration
│   ├── db.ts                         # MongoDB/Mongoose connection
│   ├── redis.ts                      # Redis client setup
│   ├── razorpay.ts                   # Razorpay payment gateway
│   └── jwt.ts                        # JWT configuration
├── constants/                        # Constants
│   ├── categories.ts                 # Product categories
│   ├── payment-methods.ts            # Payment methods
│   └── notification-types.ts         # Notification types
├── hooks/                            # Custom React hooks
│   ├── useAuth.ts                    # Auth state and JWT handling
│   ├── useCart.ts                    # Cart management (Redux Toolkit)
│   ├── useProducts.ts                # Product fetching (Redis cached)
│   ├── useAdmin.ts                   # Admin panel logic
│   ├── useNotifications.ts           # Notification handling
│   └── useMap.ts                     # Leaflet map integration
├── lib/                              # Utility functions
│   ├── api.ts                        # API client (fetch with CSRF)
│   ├── auth.ts                       # JWT auth utilities
│   ├── cart.ts                       # Cart utilities
│   ├── products.ts                   # Product utilities
│   ├── notifications.ts              # Notification utilities
│   ├── security.ts                   # Input sanitization, CSRF
│   └── redis.ts                      # Redis caching utilities
├── models/                           # Mongoose models
│   ├── User.ts                       # User schema
│   ├── Product.ts                    # Product schema
│   ├── Category.ts                   # Category schema
│   ├── Order.ts                      # Order schema
│   ├── Address.ts                    # Address schema
│   ├── Content.ts                    # Content schema
│   ├── Transaction.ts                # Transaction schema
│   └── Notification.ts               # Notification schema
├── providers/                        # React context providers
│   ├── AuthProvider.tsx              # Auth context (JWT)
│   ├── CartProvider.tsx              # Cart context (Redux Toolkit)
│   ├── ThemeProvider.tsx             # Theme context (shadcn/ui)
│   └── NotificationProvider.tsx      # Notification context
├── schemas/                          # Zod validation schemas
│   ├── auth.schema.ts                # Auth validation
│   ├── product.schema.ts             # Product validation
│   ├── checkout.schema.ts            # Checkout validation
│   ├── admin.schema.ts               # Admin validation
│   └── notification.schema.ts        # Notification validation
├── store/                            # Redux Toolkit
│   ├── slices/                       # Redux slices
│   │   ├── authSlice.ts              # Auth state
│   │   ├── cartSlice.ts              # Cart state
│   │   ├── productSlice.ts           # Product state
│   │   ├── adminSlice.ts             # Admin state
│   │   └── notificationSlice.ts      # Notification state
│   └── store.ts                      # Redux store configuration
├── styles/                           # Styling
│   ├── globals.css                   # Global CSS (Tailwind, shadcn/ui)
│   └── tailwind.config.js            # Tailwind configuration
├── types/                            # TypeScript types
│   ├── auth.d.ts                     # Auth types
│   ├── cart.d.ts                     # Cart types
│   ├── product.d.ts                  # Product types
│   ├── user.d.ts                     # User types
│   ├── admin.d.ts                    # Admin types
│   ├── notification.d.ts             # Notification types
├── utils/                            # General utilities
│   ├── formatters.ts                 # Currency, date formatting
│   ├── validators.ts                 # Zod helper functions
│   ├── map-utils.ts                  # Leaflet map utilities
│   ├── api-utils.ts                  # API request helpers
│   └── rate-limiter.ts               # Rate limiting logic
├── middleware.ts                     # Next.js middleware (JWT, CSRF, rate limiting)
├── public/                           # Static assets
│   ├── images/                       # Logos, banners, product images
│   ├── fonts/                        # Custom fonts
│   └── favicon.ico                   # Site favicon
├── package.json                      # Dependencies
├── next.config.js                    # Next.js configuration
├── tsconfig.json                     # TypeScript configuration
├── .env.local                        # Environment variables
└── README.md                         # Project documentation
```


## Structure Explanation

Implementation Details

### Frontend
Next.js 15 with App Router: Uses route groups ((admin), (auth), (main)) for organized routing. Each group has a dedicated layout.tsx for consistent UI.

React Hooks and Context: Custom hooks in hooks/ (e.g., useAuth.ts, useCart.ts) and context providers in providers/ (e.g., AuthProvider.tsx) manage state and side effects.

Redux Toolkit: Centralized state management in store/ with slices for auth, cart, products, admin, and notifications. Configured in store.ts.

shadcn/ui & Acertinity UI: UI components from shadcn/ui (e.g., DataTable, forms) and Acertinity UI (e.g., hero sections, charts) for polished, accessible design. Integrated in components/.

Zod: Form validation schemas in schemas/ (e.g., auth.schema.ts, product.schema.ts) ensure robust input validation across forms.

Map Integration: Leaflet is used for map functionality (e.g., AddressSelector.tsx, useMap.ts) for address selection with lightweight performance. Configured in map-utils.ts.

### Backend
Next.js API Routes: API endpoints in app/api/ handle all backend logic, secured with JWT and CSRF protection. Rate limiting is applied via middleware.ts.

MongoDB with Mongoose: Models in models/ (e.g., User.ts, Product.ts) define MongoDB schemas. Connection configured in config/db.ts.

Redis: Caching for product and dashboard data in lib/redis.ts. Configured in config/redis.ts.

JWT Authentication: Implemented in lib/auth.ts and config/jwt.ts. Used in API routes and protected via middleware.ts.

Rate Limiting: Implemented in utils/rate-limiter.ts and applied in middleware.ts to prevent abuse.


### Security
CSRF Protection: Integrated in lib/security.ts and applied to API routes (e.g., auth/login/route.ts) using tokens.

Input Sanitization: Handled in lib/security.ts to clean user inputs before processing.

Secure API Endpoints: JWT verification in middleware.ts ensures only authenticated requests access protected routes (e.g., api/admin/*).

Payment Tokenization: Implemented in app/api/checkout/route.ts using Razorpay (configured in config/razorpay.ts) to securely handle payments.


## First, run the development server:

```bash
npm run dev
# or
yarn dev
# or 
pnpm dev
# or
bun dev
```
