```python
langfuse:
  salt:
    value: "CHANGE_ME_SALT"

  nextauth:
    secret:
      value: "CHANGE_ME_NEXTAUTH"

  encryptionKey:
    value: "CHANGE_ME_ENCRYPTION"

  web:
    replicaCount: 1

  worker:
    replicaCount: 1


# -------------------------
# PostgreSQL (single node)
# -------------------------
postgresql:
  enabled: true

  auth:
    username: langfuse
    password: "langfuse123"
    database: langfuse

  primary:
    persistence:
      enabled: true
      size: 5Gi


# -------------------------
# Redis (standalone)
# -------------------------
redis:
  architecture: standalone

  master:
    persistence:
      enabled: true
      size: 2Gi


# -------------------------
# ClickHouse (single node)
# -------------------------
clickhouse:
  shards: 1
  replicaCount: 1

  auth:
    username: default
    password: "clickhouse123"

  zookeeper:
    enabled: false

  persistence:
    enabled: true
    size: 10Gi


# -------------------------
# MinIO (single node)
# -------------------------
minio:
  mode: standalone

  auth:
    rootUser: minio
    rootPassword: minio123

  persistence:
    enabled: true
    size: 5Gi
