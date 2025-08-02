FROM python:3.12-slim

WORKDIR /app

# Replace Debian sources.list if you want (optional)
# RUN echo "deb http://mirrors.aliyun.com/debian bookworm main contrib non-free non-free-firmware" > /etc/apt/sources.list && \
#     echo "deb http://mirrors.aliyun.com/debian bookworm-updates main contrib non-free non-free-firmware" >> /etc/apt/sources.list && \
#     echo "deb http://mirrors.aliyun.com/debian-security bookworm-security main contrib non-free non-free-firmware" >> /etc/apt/sources.list

# Install OS dependencies for Python packages, build tools, and other libs
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    gcc \
    libffi-dev \
    libssl-dev \
    libxml2-dev \
    libxslt1-dev \
    libjpeg-dev \
    zlib1g-dev \
    libpq-dev \
    python3-dev \
    pkg-config \
    libcairo2-dev \
    libgirepository1.0-dev \
    gir1.2-gtk-3.0 \
    libcups2-dev \
    libzbar0 \
    && rm -rf /var/lib/apt/lists/*

# Set environment variables passed during build time
ARG GOOGLE_APP_PASSWORD
ARG GOOGLE_CLIENT_ID

ENV GOOGLE_APP_PASSWORD=$GOOGLE_APP_PASSWORD
ENV GOOGLE_CLIENT_ID=$GOOGLE_CLIENT_ID

# Copy your Python dependency file
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Expose port
EXPOSE 8000

# Run your Django app
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
