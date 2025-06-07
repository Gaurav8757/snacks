This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Folder Sturcture 
```
nastakhasta-app/
├── app/                               # Next.js app router
│   ├── (admin)/                      # Admin routes group
│   │   ├── layout.tsx                # Admin layout with sidebar/navigation
│   │   ├── dashboard/                # Admin dashboard
│   │   │   └── page.tsx              # Dashboard with analytics
│   │   ├── users/                    # User management
│   │   │   ├── page.tsx              # Users list
│   │   │   └── [userId]/             # Single user view/edit
│   │   │       └── page.tsx
│   │   ├── products/                 # Product management
│   │   │   ├── page.tsx              # Products list
│   │   │   ├── new/                  # Create new product
│   │   │   │   └── page.tsx
│   │   │   └── [productId]/          # Edit product
│   │   │       └── page.tsx
│   │   ├── orders/                   # Order management
│   │   │   ├── page.tsx              # Orders list
│   │   │   └── [orderId]/            # Single order details
│   │   │       └── page.tsx
│   │   ├── content/                  # Content management
│   │   │   ├── pages/                # Manage static pages
│   │   │   │   └── page.tsx
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
│   │   │       └── page.tsx
│   │   ├── notifications/            # Admin notifications
│   │   │   ├── page.tsx              # Notifications list
│   │   │   └── [notificationId]/     # Notification details
│   │   │       └── page.tsx
│   ├── (auth)/                       # Authentication routes
│   │   ├── layout.tsx                # Auth layout
│   │   ├── login/                    # Login page
│   │   │   ├── page.tsx
│   │   │   └── otp-verification/     # OTP verification for login
│   │   │       └── page.tsx
│   │   └── register/                 # Registration page
│   │       ├── page.tsx
│   │       └── otp-verification/     # OTP verification for registration
│   │           └── page.tsx
│   ├── (main)/                       # Customer-facing routes
│   │   ├── layout.tsx                # Main layout with header/footer
│   │   ├── page.tsx                  # Home page
│   │   ├── account/                  # User account section
│   │   │   ├── profile/              # Profile management
│   │   │   │   └── page.tsx
│   │   │   ├── addresses/            # Address book
│   │   │   │   └── page.tsx
│   │   │   └── orders/               # User orders
│   │   │       └── [orderId]/        # Single order view
│   │   │           └── page.tsx
│   │   ├── cart/                     # Shopping cart
│   │   │   └── page.tsx
│   │   ├── checkout/                 # Checkout process
│   │   │   ├── address/              # Address selection
│   │   │   │   └── page.tsx
│   │   │   ├── payment/              # Payment method selection
│   │   │   │   └── page.tsx
│   │   │   └── confirmation/         # Order confirmation
│   │   │       └── page.tsx
│   │   ├── products/                 # Product catalog
│   │   │   ├── page.tsx              # All products
│   │   │   └── [category]/           # Category view
│   │   │       └── [productId]/      # Single product view
│   │   │           └── page.tsx
│   │   ├── track-order/              # Order tracking
│   │   │   └── [orderId]/            # Track specific order
│   │   │       └── page.tsx
│   │   ├── notifications/            # User notifications
│   │   │   ├── page.tsx              # Notifications list
│   │   │   └── [notificationId]/     # Notification details
│   │   │       └── page.tsx
│   ├── api/                          # API routes
│   │   ├── admin/                    # Admin API endpoints
│   │   │   ├── dashboard/            # Dashboard data
│   │   │   │   └── route.ts
│   │   │   ├── users/                # User management
│   │   │   │   └── route.ts
│   │   │   ├── products/             # Product management
│   │   │   │   └── route.ts
│   │   │   ├── orders/               # Order management
│   │   │   │   └── route.ts
│   │   │   ├── content/              # Content management
│   │   │   │   └── route.ts
│   │   │   ├── funds/                # Fund management
│   │   │   │   └── route.ts
│   │   │   └── notifications/        # Admin notifications
│   │   │       ├── route.ts          # Notifications list endpoint
│   │   │       └── [id]/             # Single notification endpoint
│   │   │           └── route.ts
│   │   ├── auth/                     # Authentication APIs
│   │   │   ├── login/                # Login endpoint
│   │   │   │   └── route.ts
│   │   │   ├── register/             # Registration endpoint
│   │   │   │   └── route.ts
│   │   │   └── verify-otp/           # OTP verification endpoint
│   │   │       └── route.ts
│   │   ├── cart/                     # Cart operations
│   │   │   └── route.ts
│   │   ├── checkout/                 # Checkout operations
│   │   │   └── route.ts
│   │   ├── orders/                   # Order operations
│   │   │   └── route.ts
│   │   ├── products/                 # Product data
│   │   │   └── route.ts
│   │   ├── user/                     # User data
│   │   │   └── route.ts
│   │   └── notifications/            # User notifications
│   │       ├── route.ts              # Notifications list endpoint
│   │       └── [id]/                 # Single notification endpoint
│   │           └── route.ts
│   ├── layout.tsx                    # Root layout
│   └── page.tsx                      # Root home page (optional redirect)
├── components/                       # Reusable components
│   ├── admin/                        # Admin-specific components
│   │   ├── DashboardCards.tsx        # Dashboard summary cards
│   │   ├── AnalyticsCharts.tsx       # Data visualization charts
│   │   ├── UserTable.tsx             # User management table
│   │   ├── ProductForm.tsx           # Product CRUD form
│   │   ├── OrderDetails.tsx          # Order details view
│   │   ├── ContentEditor.tsx         # WYSIWYG content editor
│   │   ├── FundReports.tsx           # Financial reports
│   │   └── AdminNotificationAlert.tsx # Admin notification alerts
│   ├── auth/                         # Authentication components
│   │   ├── LoginForm.tsx             # Login form
│   │   ├── RegisterForm.tsx          # Registration form
│   │   └── OTPInput.tsx              # OTP input component
│   ├── cart/                         # Cart components
│   │   ├── CartItem.tsx              # Individual cart item
│   │   └── CartSummary.tsx           # Cart totals and summary
│   ├── checkout/                     # Checkout components
│   │   ├── AddressForm.tsx           # Address input form
│   │   ├── PaymentMethods.tsx        # Payment method selection
│   │   └── OrderSummary.tsx          # Checkout order summary
│   ├── products/                     # Product-related components
│   │   ├── ProductCard.tsx           # Product preview card
│   │   ├── ProductDetails.tsx        # Detailed product view
│   │   └── ProductVariations.tsx     # Product variants (e.g., size, color)
│   ├── notifications/                # Notification components
│   │   ├── NotificationBell.tsx      # Notification indicator icon
│   │   ├── NotificationList.tsx      # Notifications dropdown/list
│   │   ├── NotificationItem.tsx      # Single notification item
│   ├── ui/                           # General UI components
│   │   ├── Header.tsx                # Site header
│   │   ├── Footer.tsx                # Site footer
│   │   ├── Navbar.tsx                # Navigation bar
│   │   └── RatingStars.tsx           # Product rating stars
│   └── shared/                       # Shared reusable components
│       ├── AddressSelector.tsx       # Address selection with map
│       └── Button.tsx                # Reusable button component
├── config/                           # Configuration files
│   ├── db.ts                         # Database connection (e.g., Prisma)
│   ├── redis.ts                      # Redis configuration
│   └── razorpay.ts                   # Payment gateway configuration
├── constants/                        # Application constants
│   ├── categories.ts                 # Product categories
│   ├── payment-methods.ts            # Available payment methods
│   └── notification-types.ts         # Notification types
├── hooks/                            # Custom React hooks
│   ├── useAuth.ts                    # Authentication hooks
│   ├── useCart.ts                    # Cart management hooks
│   ├── useProducts.ts                # Product fetching hooks
│   ├── useAdmin.ts                   # Admin panel hooks
│   └── useNotifications.ts           # Notification hooks
├── lib/                              # Utility functions
│   ├── api.ts                        # API client utilities
│   ├── auth.ts                       # Authentication utilities
│   ├── cart.ts                       # Cart utilities
│   ├── products.ts                   # Product utilities
│   ├── admin.ts                      # Admin utilities
│   └── notifications.ts              # Notification utilities
├── models/                           # Database models
│   ├── User.ts                       # User model
│   ├── Product.ts                    # Product model
│   ├── Category.ts                   # Category model
│   ├── Order.ts                      # Order model
│   ├── Address.ts                    # Address model
│   ├── Content.ts                    # Content model
│   ├── Transaction.ts                # Transaction model
│   └── Notification.ts               # Notification model
├── providers/                        # Context providers
│   ├── AuthProvider.tsx              # Authentication context
│   ├── CartProvider.tsx              # Cart context
│   ├── ThemeProvider.tsx             # Theme context
│   └── NotificationProvider.tsx      # Notification context
├── schemas/                          # Validation schemas (Zod or similar)
│   ├── auth.schema.ts                # Auth validation
│   ├── product.schema.ts             # Product validation
│   ├── checkout.schema.ts            # Checkout validation
│   ├── admin.schema.ts               # Admin validation
│   └── notification.schema.ts        # Notification validation
├── store/                            # Redux state management
│   ├── slices/                       # Redux slices
│   │   ├── authSlice.ts              # Auth state
│   │   ├── cartSlice.ts              # Cart state
│   │   ├── productSlice.ts           # Product state
│   │   ├── adminSlice.ts             # Admin state
│   │   └── notificationSlice.ts      # Notification state
│   └── store.ts                      # Redux store configuration
├── styles/                           # Styling
│   ├── globals.css                   # Global CSS and variables
│   └── tailwind.config.js            # Tailwind CSS configuration
├── types/                            # TypeScript types
│   ├── auth.d.ts                     # Auth types
│   ├── cart.d.ts                     # Cart types
│   ├── product.d.ts                  # Product types
│   ├── user.d.ts                     # User types
│   ├── admin.d.ts                    # Admin types
│   └── notification.d.ts             # Notification types
├── utils/                            # General utilities
│   ├── formatters.ts                 # Data formatting (e.g., currency, date)
│   ├── validators.ts                 # Validation helpers
│   ├── map-utils.ts                  # Map-related utilities
│   └── api-utils.ts                  # API request helpers
├── public/                           # Static assets
│   ├── images/                       # Images (e.g., logos, banners)
│   ├── fonts/                        # Custom fonts
│   └── favicon.ico                   # Site favicon
├── package.json                      # Project dependencies
├── next.config.js                    # Next.js configuration
├── tsconfig.json                     # TypeScript configuration
└── README.md                         # Project documentation
```


### Structure Explanation

app/: Uses Next.js App Router with route groups ((admin), (auth), (main)) to separate admin, authentication, and customer-facing routes. Each group has its own layout.tsx for consistent styling and navigation.



components/: Organized by feature (e.g., admin, auth, notifications) with a shared folder for reusable components across the app. Includes UI components like Header.tsx and Footer.tsx.



config/: Centralizes configuration for database, Redis, and payment gateways (e.g., Razorpay).



constants/: Stores static data like product categories and notification types.



hooks/: Custom React hooks for managing state and side effects, grouped by feature.



lib/: Utility functions for API calls, authentication, and notifications.



models/: Database models (e.g., Prisma schemas) for entities like users, products, and notifications.



providers/: React context providers for global state (auth, cart, notifications).



schemas/: Validation schemas (e.g., using Zod) for form and API input validation.



store/: Redux store and slices for state management, including a new notificationSlice.ts.



styles/: Global CSS and Tailwind configuration for consistent styling.



types/: TypeScript type definitions for type safety across the app.



utils/: General-purpose utilities for formatting, validation, and API helpers.



public/: Static assets like images and fonts.



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

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.js`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
