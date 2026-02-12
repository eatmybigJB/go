```python

kubectl patch storageclass standard \
  -p '{"volumeBindingMode":"Immediate"}'

