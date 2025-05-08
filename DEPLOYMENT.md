# Deployment Guide

This document outlines the steps to deploy the Photographer Portfolio application to a production environment.

## Option 1: Docker Deployment

### Prerequisites
- Docker and Docker Compose installed
- Domain name configured
- SSL certificates (recommended for production)

### Steps

1. Clone the repository on your server:
   ```
   git clone https://github.com/yourusername/photographer-portfolio.git
   cd photographer-portfolio
   ```

2. Configure environment variables:
   Update the `.env` files in both frontend and backend directories with production values.

3. Build and start the Docker containers:
   ```
   docker-compose up -d
   ```

4. The application should now be running on your server.

## Option 2: Traditional Deployment

### Backend Deployment

1. Set up a Node.js environment on your server
2. Clone the repository and navigate to the backend directory
3. Install dependencies: `npm install --production`
4. Configure environment variables for production
5. Start the server: `npm start`
6. Consider using PM2 or similar for process management: `pm2 start src/index.js --name "photographer-api"`

### Frontend Deployment

1. Build the React application: `npm run build`
2. Deploy the contents of the `build` directory to your web server (Nginx, Apache, etc.)
3. Configure your web server to serve the static files and proxy API requests to the backend server

### Nginx Configuration Example

server {
    listen 80;
    server_name yourdomain.com;
    
    # Redirect to HTTPS
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name yourdomain.com;
    
    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;
    
    # Serve frontend static files
    location / {
        root /path/to/frontend/build;
        try_files $uri /index.html;
    }
    
    # Proxy API requests to backend
    location /api {
        proxy_pass http://localhost:5000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

## Database Backup

Set up regular MongoDB backups using a cron job:

0 0 * * * mongodump --uri="mongodb://username:password@localhost:27017/photographer_db" --out=/path/to/backup/directory/$(date +\%Y-\%m-\%d)

## Monitoring

Consider setting up monitoring with tools like:
- PM2 for Node.js process monitoring
- Prometheus and Grafana for system monitoring
- Sentry for error tracking
