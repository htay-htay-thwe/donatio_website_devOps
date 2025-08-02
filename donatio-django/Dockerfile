FROM python:3.12-slim

WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends libzbar0 && rm -rf /var/lib/apt/lists/*

ARG GOOGLE_APP_PASSWORD
ARG GOOGLE_CLIENT_ID

ENV GOOGLE_APP_PASSWORD=$GOOGLE_APP_PASSWORD
ENV GOOGLE_CLIENT_ID=$GOOGLE_CLIENT_ID

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
