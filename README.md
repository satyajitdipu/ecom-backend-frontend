# SHOPX E-commerce Backend

A modern, feature-rich Node.js backend for e-commerce applications with product management, order processing, payment integration, and an admin dashboard.

## Features

- **Product Management**: Create, read, update, and delete products
- **Order Processing**: Handle customer orders with various payment statuses
- **Payment Integration**: Razorpay payment gateway integration
- **Admin Dashboard**: Comprehensive admin interface for managing products, orders, and analytics
- **Email Notifications**: Automated email notifications for order status updates
- **Database Integration**: MySQL database for data persistence

## Project Structure

```
├── controllers/       # Business logic for handling requests
│   ├── orderController.js
│   └── productController.js
├── models/           # Database connection and models
│   └── db.js
├── routes/           # API route definitions
│   ├── adminRoutes.js
│   ├── orderRoutes.js
│   ├── paymentRoutes.js
│   └── productRoutes.js
├── public/           # Static files
│   └── admin/        # Admin dashboard interface
│       └── dashboard.html
├── utils/            # Utility functions
│   └── emailService.js
├── .env              # Environment variables (create this file)
├── server.js         # Application entry point
└── package.json      # Project dependencies
```

## API Endpoints

### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get a specific product
- `POST /api/products` - Create a new product
- `PUT /api/products/:id` - Update a product
- `DELETE /api/products/:id` - Delete a product

### Orders
- `POST /api/orders` - Create a new order (with payment link)
- `GET /api/payment/order/:orderId` - Get order details

### Payments
- `POST /api/payment/save-payment` - Save payment details after Razorpay payment

### Admin
- `GET /api/admin/products` - Get all products (admin)
- `GET /api/admin/orders` - Get all orders (admin)
- `GET /api/admin/orders/:id` - Get order details (admin)
- `PATCH /api/admin/orders/:id/status` - Update order status (admin)
- `GET /api/admin/stats` - Get dashboard statistics (admin)
- `GET /admin` - Access the admin dashboard

## Database Schema

### Table: `product`
| Field        | Type              | Description                |
|--------------|-------------------|----------------------------|
| id           | int (PK, AI)      | Product ID                 |
| name         | varchar(255)      | Product name               |
| description  | text              | Product description        |
| price        | decimal(10,2)     | Product price              |
| variant      | varchar(255)      | Product variant            |
| inventory    | int               | Inventory count            |
| image_url    | varchar(500)      | Product image URL          |
| category     | varchar(100)      | Product category           |
| is_new       | tinyint(1)        | Is new product             |
| is_hot       | tinyint(1)        | Is hot product             |
| rating       | decimal(2,1)      | Product rating             |
| reviews      | int               | Number of reviews          |
| colors       | longtext (JSON)   | Available colors           |

### Table: `orders`
| Field      | Type           | Description         |
|------------|----------------|---------------------|
| id         | varchar(100)   | Order ID (UUID)     |
| product_id | int            | Product ID          |
| full_name  | varchar(255)   | Customer name       |
| email      | varchar(255)   | Customer email      |
| phone      | varchar(20)    | Customer phone      |
| address    | text           | Address             |
| city       | varchar(100)   | City                |
| state      | varchar(100)   | State               |
| zip        | varchar(20)    | Zip code            |
| variant    | varchar(50)    | Product variant     |
| quantity   | int            | Quantity            |
| total      | decimal(10,2)  | Total amount        |
| status     | varchar(50)    | Order status        |
| created_at | timestamp      | Order creation time |

### Table: `payment`
| Field               | Type           | Description                |
|---------------------|----------------|----------------------------|
| id                  | int (PK, AI)   | Payment ID                 |
| order_id            | varchar(255)   | Order ID                   |
| razorpay_payment_id | varchar(255)   | Razorpay payment ID        |
| razorpay_order_id   | varchar(255)   | Razorpay order ID          |
| razorpay_signature  | text           | Razorpay signature         |
| status              | varchar(50)    | Payment status             |
| created_at          | timestamp      | Payment creation time      |

## Setup Guide

### Prerequisites
- Node.js (v14 or higher)
- MySQL database
- Razorpay account (for payment processing)
- SMTP server access (for email notifications)

### Installation

1. Clone the repository
   ```sh
   git clone https://github.com/satyajitdipu/ecommers-backend
   cd ecommers-backend
   ```

2. Install dependencies
   ```sh
   npm install
   ```

3. Create a `.env` file in the root directory with the following variables:
   ```
   # Server
   PORT=5000

   # Database
   DB_HOST=localhost
   DB_USER=your_db_user
   DB_PASSWORD=your_db_password
   DB_NAME=ecommerce

   # Razorpay
   RAZORPAY_KEY_ID=your_razorpay_key_id
   RAZORPAY_KEY_SECRET=your_razorpay_key_secret

   # Email
   MAIL_HOST=smtp.example.com
   MAIL_PORT=587
   MAIL_USER=your_email@example.com
   MAIL_PASS=your_email_password
   ```

4. Set up the database
   - Import the [`ecommerce (1).sql`](ecommerce%20(1).sql) file into your MySQL server to create the required tables and sample data.

5. Start the server
   ```sh
   npm start
   ```

6. Access the admin dashboard
   - URL: `http://localhost:5000/admin`
   - Default credentials: username: `admin`, password: `admin123`

## Development

### Adding New Features

1. Create new route files in the `routes/` directory
2. Implement controller logic in the `controllers/` directory
3. Update the `server.js` file to include new routes

### Customizing Email Templates

Modify the email HTML templates in the [`orderController.js`](controllers/orderController.js) file to customize email notifications.

## Credits

- Developed by Satyajit Sahoo
- UI Design: Satyajit Sahoo
- Icons: Bootstrap Icons
- Charts: Chart.js

## License

ISC
# ShoeX - Premium Sneaker E-commerce Platform 👟

A modern, responsive e-commerce platform built with React, featuring a sleek dark/light theme, advanced animations, and a premium user experience for sneaker enthusiasts.

## 🚀 Features

- **Modern UI/UX**: Glassmorphism design with smooth animations
- **Dark/Light Theme**: Toggle between cyberpunk dark mode and clean light mode
- **Responsive Design**: Works seamlessly across all devices
- **Advanced Cart System**: Persistent cart with local storage
- **Dynamic Navigation**: Smooth scrolling navigation with dynamic island effect
- **Product Showcase**: Interactive 3D product cards with hover effects
- **Real-time Notifications**: Toast notifications for user actions
- **Page Routing**: Multi-page application with React Router
- **Animated Components**: Framer Motion powered animations throughout

## 🛠️ Tech Stack

### Core Technologies
- **React** (18.2.0) - Frontend framework
- **React Router DOM** - Client-side routing
- **JavaScript (ES6+)** - Programming language
- **CSS3** - Styling with custom properties

### UI Components & Styling
- **Hero UI/React** (@heroui/react) - Modern UI component library
- **Tailwind CSS** - Utility-first CSS framework
- **Framer Motion** - Animation library for React
- **Lucide React** - Icon library

### Additional Libraries
- **React Hot Toast** - Toast notifications
- **React Portal** - Modal and overlay management

## 📦 Installation Guide

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn package manager

### Step-by-Step Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/shoex-ecommerce.git
   cd shoex-ecommerce
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```
   or
   ```bash
   yarn install
   ```

3. **Install required packages**
   ```bash
   npm install @heroui/react framer-motion lucide-react react-hot-toast react-router-dom
   ```

4. **Install Tailwind CSS**
   ```bash
   npm install -D tailwindcss postcss autoprefixer
   npx tailwindcss init -p
   ```

5. **Start the development server**
   ```bash
   npm start
   ```

6. **Open your browser**
   Navigate to [http://localhost:3000](http://localhost:3000)

## 🏗️ Project Structure

```
src/
├── components/
│   ├── Navigation.jsx           # Dynamic navigation with island effect
│   ├── HeroSection.jsx          # Landing page hero section
│   ├── ProductShowcase.jsx      # Product grid with 3D cards
│   ├── FeaturesSection.jsx      # Features showcase
│   ├── Footer.jsx              # Site footer
│   ├── CartDrawer.jsx          # Sliding cart drawer
│   └── ThemeProvider.jsx       # Dark/light theme context
├── context/
│   └── CartContext.jsx         # Shopping cart state management
├── pages/
│   ├── LandingPage.jsx         # Homepage
│   ├── MenPage.jsx             # Men's products
│   ├── WomenPage.jsx           # Women's products
│   ├── SneakersPage.jsx        # Premium sneakers
│   ├── SalePage.jsx            # Sale products with countdown
│   ├── AboutPage.jsx           # About us page
│   ├── ContactPage.jsx         # Contact form and info
│   └── NotFoundPage.jsx        # 404 error page
├── App.jsx                     # Main app component with routing
├── index.js                    # React entry point
└── index.css                   # Global styles and animations
```

## 🎨 Components Overview

### Core Components
- **Navigation**: Dynamic island navigation with scroll effects
- **ThemeProvider**: Context for dark/light theme switching
- **CartContext**: Global state management for shopping cart

### Page Components
- **LandingPage**: Hero section, product showcase, features
- **ProductPages**: Men, Women, Sneakers with filtering
- **SalePage**: Products with discount countdown timer
- **AboutPage**: Company information and team
- **ContactPage**: Contact form with validation
- **NotFoundPage**: Custom 404 error page

### UI Components
- **ProductShowcase**: 3D product cards with animations
- **CartDrawer**: Slide-out cart with quantity controls
- **HeroSection**: Animated landing section
- **FeaturesSection**: Company features highlight

## 🎯 Key Features Breakdown

### Theme System
- Cyberpunk dark mode with neon colors
- Clean light mode with professional styling
- Smooth transitions between themes
- Persistent theme preference

### Shopping Cart
- Add/remove products
- Quantity management
- Price calculations
- Local storage persistence
- Toast notifications

### Animations
- Page transitions with Framer Motion
- Hover effects on product cards
- Scroll-triggered animations
- Loading skeletons
- Micro-interactions

### Responsive Design
- Mobile-first approach
- Tablet and desktop optimization
- Touch-friendly interactions
- Adaptive navigation

## 🚀 Available Scripts

### `npm start`
Runs the app in development mode at [http://localhost:3000](http://localhost:3000)

### `npm test`
Launches the test runner in interactive watch mode

### `npm run build`
Builds the app for production to the `build` folder

### `npm run eject`
**Warning**: This is a one-way operation. Ejects from Create React App configuration.

## 🎨 Customization

### Theme Colors
Edit `tailwind.config.js` to customize the color palette:
```javascript
module.exports = {
  theme: {
    extend: {
      colors: {
        'neon-blue': '#00F5FF',
        'neon-yellow': '#FFFF00',
        'neon-purple': '#FF00FF',
      }
    }
  }
}
```

### Animations
Modify animations in `src/index.css` or component-level Framer Motion variants.

## 📱 Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## 🐛 Troubleshooting

### Common Issues

1. **Dependencies not installing**
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   ```

2. **Tailwind classes not working**
   - Check `tailwind.config.js` configuration
   - Ensure Tailwind directives are imported in `index.css`

3. **Animations not smooth**
   - Enable GPU acceleration in browser
   - Check for reduced motion preferences

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Credits

**Developed by:** [Satyajit Sahoo](https://github.com/satyajitsahoo)  
Special thanks to Satyajit Sahoo for the incredible design vision and development expertise that brought this premium e-commerce platform to life.

### Additional Credits
- **Hero UI** - For the beautiful component library
- **Framer Motion** - For smooth animations
- **Lucide React** - For the icon set
- **Unsplash** - For product placeholder images

## 📞 Support

---

**Built with ❤️ by Satyajit Sahoo**

Enjoy building your sneaker empire! 👟✨