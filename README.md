```python
SELECT
    current_user,
    current_database(),
    inet_server_addr(),
    version();

from fastapi import FastAPI, HTTPException
import psycopg2
from psycopg2.extras import RealDictCursor
from azure.identity import DefaultAzureCredential

app = FastAPI()


def get_db_connection():
    # 1. 获取 Azure AD token
    credential = DefaultAzureCredential()
    token = credential.get_token(
        "https://ossrdbms-aad.database.windows.net/.default"
    ).token

    # 2. PostgreSQL 连接信息
    hostname = "pgsql-uksouth-kms-sc-gpt-dev-dev.postgres.database.azure.com"
    database = "postgres"
    username = "vmss_uai_uksouth"

    # psycopg2 需要 password=token，不能带 <>
    conn = psycopg2.connect(
        host=hostname,
        dbname=database,
        user=username,
        password=token,
        sslmode="require",
        cursor_factory=RealDictCursor,
    )
    return conn


@app.get("/health/db")
def check_db():
    try:
        conn = get_db_connection()
        cur = conn.cursor()

        cur.execute("""
            SELECT
                current_user,
                current_database() AS database,
                inet_server_addr() AS server_ip,
                version();
        """)

        result = cur.fetchone()

        cur.close()
        conn.close()

        return {
            "status": "ok",
            "db_info": result
        }

    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

/root/venv/bin/python -m pip install fastapi uvicorn psycopg2-binary azure-identity
/root/venv/bin/uvicorn main:app --host 0.0.0.0 --port 8089
curl http://127.0.0.1:8089/health/db
