# use the official lightweight Nginx image as a base
FROM nginx:stable-alpine

# copy our custom Nginx configuration
COPY nginx/nginx.conf /etc/nginx/nginx.conf

# create the html directory
RUN mkdir -p /usr/share/nginx/html

# fix permissions so Nginx (running as user nginx) can read the files
RUN chown -R nginx:nginx /usr/share/nginx/html

# No CMD needed - base image handles it