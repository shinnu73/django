# Use the official Nginx image as a parent image
FROM nginx:latest

# Remove default Nginx configuration
RUN rm /etc/nginx/conf.d/default.conf

# Copy the custom Nginx configuration file
COPY nginx/nginx.conf /etc/nginx/conf.d/

# Expose ports
EXPOSE 80

