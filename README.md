# QuickCart - E-Commerce Web App

A modern, full-stack e-commerce platform built with Next.js 15, React 19, and MongoDB. Features a dual-role system for customers and sellers, integrated payment processing with Stripe, and automated order management with Inngest.

## 🚀 Features

### Customer Features
- **Product Browsing**: Browse all available products with filtering and search
- **Shopping Cart**: Add, update, and manage items in cart
- **User Authentication**: Secure authentication with Clerk
- **Order Management**: Place orders and track order history
- **Address Management**: Save and manage multiple delivery addresses
- **Payment Processing**: Integrated Stripe payment gateway
- **Newsletter Signup**: Subscribe to promotional updates

### Seller Features
- **Seller Dashboard**: Dedicated dashboard for sellers
- **Product Management**: Add, edit, and manage product inventory
- **Order Management**: View and manage seller-specific orders
- **Sales Analytics**: Track sales and order statistics

### Backend Features
- **Automated Workflows**: Inngest for background job processing
- **Real-time Order Updates**: Order status tracking and updates
- **Image Management**: Cloudinary integration for product images
- **Database**: MongoDB for scalable data storage

## 🛠️ Tech Stack

### Frontend
- **Framework**: [Next.js 15](https://nextjs.org) with App Router
- **UI Library**: React 19
- **Styling**: [Tailwind CSS](https://tailwindcss.com)
- **State Management**: React Context API
- **HTTP Client**: Axios
- **Notifications**: React Hot Toast
- **Authentication**: [Clerk](https://clerk.com)

### Backend
- **Runtime**: Node.js
- **Database**: [MongoDB](https://www.mongodb.com)
- **ORM**: [Mongoose](https://mongoosejs.com)
- **Workflow Automation**: [Inngest](https://inngest.com)
- **Payment Gateway**: [Stripe](https://stripe.com)
- **Image Storage**: [Cloudinary](https://cloudinary.com)

### Developer Tools
- **Linting**: ESLint
- **Code Formatting**: PostCSS
- **Package Manager**: npm

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (v18 or higher)
- npm or yarn package manager
- MongoDB (local or MongoDB Atlas)

## 🔑 Environment Variables

Create a `.env.local` file in the root directory with the following variables:

```env
# Database
MONGODB_URI=your_mongodb_connection_string

# Authentication (Clerk)
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_key
CLERK_SECRET_KEY=your_clerk_secret

# Payment Processing (Stripe)
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_stripe_key
STRIPE_SECRET_KEY=your_stripe_secret

# Image Upload (Cloudinary)
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=your_cloudinary_name

# Inngest
INNGEST_SIGNING_KEY=your_inngest_key
```

## 📦 Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Ecommerce_Web_App
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   - Create a `.env.local` file in the root directory
   - Add all required environment variables (see Environment Variables section)

4. **Start the development server**
   ```bash
   npm run dev
   ```

5. **Open your browser**
   - Navigate to [http://localhost:3000](http://localhost:3000)

## 📁 Project Structure

```
Ecommerce_Web_App/
├── app/                          # Next.js App Router
│   ├── api/                      # API Routes
│   │   ├── cart/                 # Cart management endpoints
│   │   ├── order/                # Order management endpoints
│   │   ├── product/              # Product endpoints
│   │   ├── user/                 # User endpoints
│   │   ├── stripe/               # Stripe webhook
│   │   └── inngest/              # Inngest workflow endpoint
│   ├── seller/                   # Seller dashboard pages
│   │   ├── page.jsx              # Seller home
│   │   ├── orders/               # Seller orders
│   │   └── product-list/         # Seller product list
│   ├── cart/                     # Shopping cart page
│   ├── my-orders/                # Customer orders page
│   ├── all-products/             # All products listing
│   ├── product/[id]/             # Product detail page
│   └── add-address/              # Address management
├── components/                   # Reusable React components
│   ├── Navbar.jsx               # Main navigation
│   ├── ProductCard.jsx          # Product display card
│   ├── OrderSummary.jsx         # Order summary component
│   └── seller/                  # Seller-specific components
├── config/                       # Configuration files
│   ├── db.js                    # MongoDB connection
│   └── inngest.js               # Inngest workflows
├── context/                      # React Context
│   └── AppContext.jsx           # Global app state
├── models/                       # Mongoose schemas
│   ├── User.js
│   ├── Product.js
│   ├── Order.js
│   └── Address.js
├── lib/                          # Utility functions
│   └── authSeller.js            # Seller authentication middleware
├── public/                       # Static assets
├── assets/                       # App assets
├── middleware.ts                 # Next.js middleware
├── tailwind.config.mjs           # Tailwind CSS configuration
├── next.config.mjs              # Next.js configuration
└── package.json                 # Project dependencies
```

## 🚀 Available Scripts

```bash
# Start development server with Turbopack
npm run dev

# Build for production
npm run build

# Start production server
npm start

# Run ESLint to check code quality
npm run lint
```

## 🎯 API Endpoints

### Products
- `GET /api/product/list` - Get all products
- `GET /api/product/seller-list` - Get seller's products
- `POST /api/product/add` - Add new product (seller only)

### Cart
- `GET /api/cart/get` - Get user's cart
- `PUT /api/cart/update` - Update cart items

### Orders
- `POST /api/order/create` - Create new order
- `GET /api/order/list` - Get user's orders
- `GET /api/order/seller-orders` - Get seller's orders

### User
- `GET /api/user/data` - Get user profile
- `POST /api/user/add-address` - Add user address
- `GET /api/user/get-address` - Get user addresses

### Payment
- `POST /api/stripe` - Process Stripe payments
- `POST /api/order/stripe` - Stripe webhook endpoint

## 🔐 Authentication

The application uses [Clerk](https://clerk.com) for authentication:
- Secure user signup and login
- Role-based access control (Customer vs Seller)
- Protected API routes with middleware

## 💳 Payment Integration

Stripe is integrated for secure payment processing:
- PCI-compliant payment handling
- Webhook support for payment status updates
- Order status updates via Inngest workflows

## 🔄 Background Jobs

Inngest handles background tasks:
- Syncing user data from Clerk
- Processing order confirmations
- Updating order statuses
- Handling Stripe webhook events

## 🚢 Deployment

### Deploy on Vercel (Recommended)

1. Push your code to GitHub
2. Visit [Vercel](https://vercel.com)
3. Import the repository
4. Add environment variables in Vercel dashboard
5. Deploy

```bash
npm run build
```

### Deploy on Other Platforms

Ensure your platform supports:
- Node.js runtime
- MongoDB connection
- Environment variables configuration
- Webhook support for Stripe and Inngest

## 📚 Database Models

### User
- Stores user profile information
- Email, name, authentication ID from Clerk
- User addresses

### Product
- Product details, price, inventory
- Images (Cloudinary URLs)
- Seller information
- Stock management

### Order
- Order details and status
- Customer and seller information
- Order items and pricing
- Payment information

### Address
- User delivery addresses
- Multiple address support
- Address type (home, office, etc.)

## 🤝 Contributing

1. Create a feature branch (`git checkout -b feature/amazing-feature`)
2. Commit changes (`git commit -m 'Add amazing feature'`)
3. Push to branch (`git push origin feature/amazing-feature`)
4. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Troubleshooting

### MongoDB Connection Issues
- Verify `MONGODB_URI` is correct
- Check MongoDB Atlas IP whitelist
- Ensure database exists

### Clerk Authentication Issues
- Verify Clerk keys in environment variables
- Check Clerk dashboard for API configuration
- Clear browser cookies if session issues persist

### Stripe Payment Issues
- Test with Stripe test keys first
- Verify webhook URL in Stripe dashboard
- Check webhook signing key matches `STRIPE_SECRET_KEY`

### Inngest Workflow Issues
- Verify Inngest signing key
- Check Inngest dashboard for event logs
- Ensure function IDs are unique

## 📧 Support

For issues or questions:
1. Check existing GitHub issues
2. Create a new issue with detailed description
3. Include steps to reproduce the problem
4. Attach relevant error logs

---

**Happy Coding!** 🎉
