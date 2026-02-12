```python
helm install langfuse langfuse/langfuse \
  -n langfuse \
  --create-namespace \
  --set langfuse.salt.value=$(openssl rand -hex 32) \
  --set langfuse.nextauth.secret.value=$(openssl rand -hex 32)
