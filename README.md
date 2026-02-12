```python
helm install langfuse langfuse/langfuse \
  -n langfuse \
  --create-namespace \
  --set langfuse.salt=$(openssl rand -hex 32)
