```python

apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: local-path-immediate
provisioner: rancher.io/local-path
volumeBindingMode: Immediate

langfuse:
  salt:
    value: "langfuse_salt_123456789"

  nextauth:
    secret:
      value: "langfuse_nextauth_secret_123456789"

  encryptionKey:
    value: "langfuse_encryption_key_123456789"

  web:
    replicaCount: 1

  worker:
    replicaCount: 1


# -----------------------
# PostgreSQL
# -----------------------
postgresql:
  enabled: true

  auth:
    username: langfuse
    password: "postgres123"
    database: langfuse

  primary:
    persistence:
      enabled: true
      storageClass: local-path-immediate
      size: 5Gi


# -----------------------
# Redis (standalone)
# -----------------------
redis:
  architecture: standalone

  auth:
    enabled: false

  master:
    persistence:
      enabled: true
      storageClass: local-path-immediate
      size: 2Gi


# -----------------------
# ClickHouse (single node)
# -----------------------
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
    storageClass: local-path-immediate
    size: 10Gi


# -----------------------
# MinIO (S3 storage)
# -----------------------
minio:
  mode: standalone

  auth:
    rootUser: minio
    rootPassword: "minio123"

  persistence:
    enabled: true
    storageClass: local-path-immediate
    size: 5Gi
