```python

kubectl describe pvc data-langfuse-postgresql-0 -n langfuse

kubectl logs -n local-path-storage -l app=local-path-provisioner
