FROM python:3.13.2-bookworm

ENV PYTHONUNBUFFERED=1

COPY . /app
WORKDIR /app

RUN apt-get update && apt-get install -y \
    vim \
    git \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir -r requirements.txt

CMD ["./start.sh"]
