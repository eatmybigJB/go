```python
aws secretsmanager get-secret-value \
  --secret-id YOUR_SECRET_NAME \
  --query SecretString \
  --output text \
  --region eu-west-2 | jq -r '.password'
