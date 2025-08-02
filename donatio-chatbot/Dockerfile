FROM python:3.12-slim

WORKDIR /app

# Copy project files *before* syncing deps
COPY requirements.txt .

ARG GROQ_API_KEY

ENV GROQ_API_KEY=$GROQ_API_KEY

RUN pip install -r requirements.txt

# Copy the rest of your code
COPY . .

EXPOSE 8001

CMD ["uvicorn", "main:app", "--reload", "--port", "8001", "--host", "0.0.0.0"]
