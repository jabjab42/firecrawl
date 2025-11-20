# Base on offical NGINX Alpine image
FROM nginx:alpine

# Remove any existing config files
RUN rm /etc/nginx/conf.d/*

# Copy config files
# *.conf files in conf.d/ dir get included in main config
COPY ./default.conf /etc/nginx/conf.d/

# Create cache directory and set permissions
RUN mkdir -p /var/cache/nginx && chown -R nginx:nginx /var/cache/nginx

# Expose the listening port
EXPOSE 80
EXPOSE 443 

# Substitute environment variables and launch NGINX
CMD ["/bin/sh", "-c", "envsubst '${AUTH_TOKEN}' < /etc/nginx/conf.d/default.conf > /etc/nginx/conf.d/default.conf.tmp && mv /etc/nginx/conf.d/default.conf.tmp /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'"]
