FROM python:3.6-alpine

WORKDIR /app

ENV ENVIRONMENT=DEV
ENV HOST=localhost
ENV PORT=8000
ENV REDIS_HOST=localhost
ENV REDIS_PORT=6379
ENV REDIS_DB=0

ADD . .

RUN pip install -r requirements.txt

CMD ["python", "hello.py"]