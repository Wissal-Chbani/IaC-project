FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN sed -i 's/\r$//' generate-votes.sh
RUN python make-data.py
RUN apt-get update
RUN apt-get install -y apache2-utils
CMD ["sh", "generate-votes.sh"]