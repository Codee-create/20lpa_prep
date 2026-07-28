FROM nginx:alpine

# Copy custom nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Copy static assets to the default nginx public directory
COPY . /usr/share/nginx/html

# Expose port 80 for traffic
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
