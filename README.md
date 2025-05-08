# Photographer Portfolio Website

A modern, responsive portfolio website for photographers that allows them to showcase their work, sell digital copies of photos, receive orders for photo sessions, and integrate with photo printing services.

## Features

- Responsive photo gallery with filtering options
- Services section with pricing details
- Contact form for inquiries
- Client testimonials/reviews section
- Shopping cart functionality
- Secure payment processing
- Photo download capability (after purchase)
- Integration with photo printing services
- User account management

## Tech Stack

- **Frontend**: React.js with TypeScript
- **State Management**: Redux Toolkit
- **Styling**: Tailwind CSS
- **Backend**: Node.js with Express
- **Database**: MongoDB
- **Authentication**: JWT
- **Payment Processing**: Stripe
- **File Storage**: AWS S3
- **Deployment**: Docker, Nginx

## Installation and Setup

### Prerequisites

- Node.js (v16 or higher)
- MongoDB
- AWS account (for S3)
- Stripe account
- Docker (optional for deployment)

### Local Development Setup

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/photographer-portfolio.git
   cd photographer-portfolio
   ```

2. Install dependencies for both frontend and backend:
   ```
   # Install backend dependencies
   cd backend
   npm install

   # Install frontend dependencies
   cd ../frontend
   npm install
   ```

3. Set up environment variables:
   Create `.env` files in both the backend and frontend directories based on the provided `.env.example` files.

4. Start the development servers:
   ```
   # Start backend server (from the backend directory)
   npm run dev

   # Start frontend development server (from the frontend directory)
   npm start
   ```

5. The application should now be running:
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000

## Deployment

Detailed deployment instructions can be found in [DEPLOYMENT.md](DEPLOYMENT.md)

## License

MIT
