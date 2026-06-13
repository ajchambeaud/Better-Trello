FROM python:3.9-slim

# Build deps for psycopg2 (listed in requirements.txt)
RUN apt-get update \
    && apt-get install -y --no-install-recommends build-essential libpq-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Flask CLI needs to know which app to load for `flask initdb`
ENV FLASK_APP=app
ENV PORT=3400

EXPOSE 3400

# Seed sample data, then start the SocketIO/Flask server (start.py reads $PORT)
CMD ["sh", "-c", "flask initdb && python start.py"]
