FROM python:3.12-alpine

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONBUFFERED=1

RUN apk update && apk add postgresql-dev gcc python3-dev musl-dev
RUN pip install --upgrade pip

COPY . /app/
RUN pip install -r requirements.txt

EXPOSE 8000

# Lier Gunicorn à l'adresse 0.0.0.0 pour qu'il soit accessible de l'extérieur du conteneur
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "--workers", "3", "dj_postgres.wsgi:application"]
