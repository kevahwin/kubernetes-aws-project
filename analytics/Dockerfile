FROM python:3.12-slim-bullseye

USER root

WORKDIR /src

COPY ./requirements.txt requirements.txt

# Copy requirements and install dependencies
RUN apt update -y && apt install -y build-essential libpq-dev

# Install Python dependencies
RUN pip install -r requirements.txt

# Copy the application code
COPY . .

# Run the application
CMD ["python", "app.py"]
