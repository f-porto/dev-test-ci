FROM python:3.12-alpine

WORKDIR /app

COPY requirements.txt .

RUN python -m pip install --no-cache-dir --upgrade -r requirements.txt

COPY . .

ENTRYPOINT [ "python" ]
CMD [ "manage.py", "runserver", "0.0.0.0:80" ]
