```python
langfuse:
  salt:
    value: "CHANGE_ME_SALT"

  nextauth:
    secret:
      value: "CHANGE_ME_NEXTAUTH"

  encryptionKey:
    value: "CHANGE_ME_ENCRYPTION"

  # 单 worker 即可
  worker:
    replicaCount: 1

  web:
    replicaCount: 1

# -----------------------
# PostgreSQL
# -----------------------
postgresql:
  enabled: true
  auth:
    username: langfuse
    password: "langfuse"
    database: langfuse

  primary:
    persistence:
      enabled: true
      size: 5Gi

# -----------------------
# Redis (no HA)
# -----------------------
redis:
  architecture: standalone
  master:
    persistence:
      enabled: true
      size: 2Gi

# -----------------------
# ClickHouse (single node)
# -----------------------
clickhouse:
  replicaCount: 1

  shards: 1

  zookeeper:
    enabled: false

  persistence:
    enabled: true
    size: 10Gi

# -----------------------
# MinIO (single instance)
# -----------------------
minio:
  mode: standalone

  persistence:
    enabled: true
    size: 5Gi

# -----------------------
# Resource limits（避免 kind 爆内存）
# -----------------------
resources:
  requests:
    cpu: 100m
    memory: 256Mi


helm install langfuse langfuse/langfuse \
  -n langfuse \
  --create-namespace \
  -f langfuse-single-node.values.yaml
