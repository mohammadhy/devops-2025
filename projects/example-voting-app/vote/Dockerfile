FROM python:3.11-slim AS base

RUN apt-get update && \
    apt-get install -y --no-install-recommends curl && \
    rm -rf /var/lib/apt/lists/*
RUN groupadd -g 2000 appgroup && \
    useradd -u 1000 -g appgroup -s /bin/sh -d /home/appuser appuser
WORKDIR /usr/local/app

COPY requirements.txt ./requirements.txt
RUN pip install --no-cache-dir -r requirements.txt
COPY gunicorn_config.py ./gunicorn_config.py

#FROM base AS dev
#RUN pip install watchdog
#ENV FLASK_ENV=development
#CMD ["python", "app.py"]
#FROM base AS final

COPY . .
RUN chown -R appuser:appgroup /usr/local/app
USER appuser 
CMD ["gunicorn", "app:app", "-c", "/usr/local/app/gunicorn_config.py"]
