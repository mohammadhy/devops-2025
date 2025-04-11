FROM python:3.9-slim-bullseye
WORKDIR /opt/suggestion
RUN apt-get update && apt-get install --no-install-recommends -y python3-pip
COPY requirement.txt requirement.txt
RUN pip install -r requirement.txt
COPY app.py app.py
COPY .flaskenv .flaskenv
EXPOSE 5000
CMD ["python", "app.py"]

