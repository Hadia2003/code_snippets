FROM python:3.9-slim

WORKDIR /app

# Copy requirements
COPY requirements.txt /app/requirements.txt

# Install OS-level build dependencies
RUN apt-get update && \
    apt-get install -y build-essential libssl-dev libffi-dev zlib1g-dev libjpeg-dev && \
    rm -rf /var/lib/apt/lists/*

# Pin pip, setuptools, and install wheel for building old packages
RUN pip install --no-cache-dir --upgrade pip==23.2.1 setuptools==58.0.4 wheel

# Now install all requirements
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . /app

EXPOSE 5000

ENV FLASK_APP=flaskblog.py
CMD ["flask", "run", "--host=0.0.0.0"]
