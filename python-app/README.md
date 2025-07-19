# python-app


## Requirments:
```
Need Redis Be Up & Running On Port 6379
It's Hardcoded On myproject.py
Support Apm If You Need It Uncomment It On Dockerfile 
```
## Usage
```bash
docker build -t <Registery-Addres>/python-web-app:0.0.1 .
docker run -it --rm -p 80:80 python-web-app:0.0.1 
```
