FROM python:3.10-slim-buster

USER root

WORKDIR /src

# Copy requirements and install dependencies
COPY ./requirements.txt requirements.txt

RUN apt update -y && apt install -y build-essential libpq-dev
RUN pip install -r requirements.txt

# Copy the application code
COPY . .

# Set build arguments and map them to environment variables
ARG DB_PASSWORD
ARG DB_USERNAME

ENV POSTGRES_PASSWORD=$DB_PASSWORD
ENV POSTGRES_USER=$DB_USERNAME
ENV POSTGRES_DB=postgres

# Run the application
CMD ["python", "app.py"]
