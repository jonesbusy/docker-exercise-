FROM node:8.4.0

MAINTAINER Valentin Delaye <valentin.delaye@gmail.com>

COPY ["app.js", "package.json", "/opt/web-app/"]
COPY ["wait-for-it.sh", "/"]

# Create user and fix permissions
RUN adduser --system  --shell /bin/false --gid 0 web-user && \ 
    chown -R web-user:root /opt/web-app

# Run as user
USER web-user

# Working directory
WORKDIR /opt/web-app

# Install dependencies
RUN npm install

# Copy source files
COPY routes/* /opt/web-app/routes/
COPY views/* /opt/web-app/views/
COPY bin/* /opt/web-app/bin/

# Expose port
EXPOSE 3000

CMD ["node", "./bin/www"]


