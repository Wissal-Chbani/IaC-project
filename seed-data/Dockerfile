FROM python:3.9-slim
WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends apache2-utils \
    && rm -rf /var/lib/apt/lists/*

COPY make-data.py .

RUN python make-data.py

RUN sed -i 's/\r$//' generate-votes.sh

CMD ["sh", "generate-votes.sh"]
