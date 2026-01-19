```python
aws iam list-roles \
  --query "Roles[?contains(RoleName, 'Admin')].[RoleName,Arn]" \
  --output table
