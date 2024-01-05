# Use an official Python runtime as a parent image
FROM python:3.9

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set the working directory in the container
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    postgresql-client \
    libpq-dev

# Install Python dependencies
COPY requirements.txt /app/
RUN pip install --upgrade pip && pip install -r requirements.txt

# Copy the current directory contents into the container at /app
COPY . /app/

# Collect static files
RUN python3 manage.py collectstatic --noinput

#COPY nginx/nginx.conf /etc/nginx/conf.d/

# Run Gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "mydjangoapp.wsgi:application"]

