FROM python:3.9

# PostgreSQLの公式リポジトリを追加
RUN apt-get update && apt-get install -y lsb-release gnupg2
RUN echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -

# 最新のPostgreSQLクライアントとlibpqをインストール
RUN apt-get update && apt-get install -y \
    postgresql-client \
    libpq-dev

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
