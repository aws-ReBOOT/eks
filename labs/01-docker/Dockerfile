FROM python:3.7

COPY requirements.txt requirements.txt

RUN pip install --no-cache -r requirements.txt

EXPOSE 5000

CMD ["python", "server.py"]

COPY . .
