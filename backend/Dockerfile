FROM python:3.9

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

COPY . .

VOLUME ["/app/static", "/app/media"]

EXPOSE 8000

ENTRYPOINT ["sh", "-c", "\
    python manage.py migrate --noinput && \
    python manage.py collectstatic --noinput && \
    exec gunicorn kittygram_backend.wsgi:application \
      --bind 0.0.0.0:8000 \
"]