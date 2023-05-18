FROM python:3.9.3

COPY requirements.txt requirements.txt

RUN pip install --no-cache --disable-pip-version-check -r requirements.txt

EXPOSE 5000

CMD ["python3", "server.py"]

COPY . .
