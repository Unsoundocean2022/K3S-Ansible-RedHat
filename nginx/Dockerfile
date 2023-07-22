# Use the official nginx base image based on Alpine Linux
FROM nginx:stable-alpine3.17-slim

# Update the package manager and install necessary packages
RUN apk update \
    && apk add --no-cache \
       vim \
       ca-certificates

# Copy the nginx stream configuration to the container
COPY nginx.conf /etc/nginx/nginx.conf

# Set correct file permissions for nginx configuration
RUN chmod 644 /etc/nginx/nginx.conf

# Create a directory for SSL certificates (if using HTTPS)
# COPY your_ssl_cert.crt /etc/nginx/ssl/
# COPY your_ssl_cert.key /etc/nginx/ssl/

# Use strong passwords for Nginx authentication (if needed)
# RUN htpasswd -c /etc/nginx/.htpasswd username

# Disable unnecessary Nginx modules
# (Optional: Based on your specific use case, disable modules that are not required)
# RUN sed -i -e 's/# load_module/load_module/' /etc/nginx/nginx.conf

# Implement health checks for the container (if applicable)
# HEALTHCHECK --interval=30s --timeout=5s --retries=3 CMD curl -f http://localhost:6443 || exit 1

# Expose only the necessary ports (e.g., port 6443)
EXPOSE 6443

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
