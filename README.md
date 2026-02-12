```python
helm install langfuse langfuse/langfuse \
  -n langfuse \
  --create-namespace \
  --set postgresql.auth.password=123456abc \
  --set-string langfuse.salt.value=$(openssl rand -hex 32) \
  --set-string langfuse.nextauth.secret.value=$(openssl rand -hex 32) \
  --set-string langfuse.encryptionKey.value=$(openssl rand -hex 32)

