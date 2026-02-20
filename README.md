```python

TOKEN=$(az account get-access-token \
--resource https://cognitiveservices.azure.com \
--query accessToken -o tsv)


curl -v \
"https://paytechchatgptdev-uksouth.openai.azure.com/openai/deployments?api-version=2024-08-01-preview" \
-H "Authorization: Bearer $TOKEN"

curl -v \
"https://paytechchatgptdev-uksouth.openai.azure.com/openai/deployments?api-version=2024-02-15-preview" \
-H "Authorization: Bearer $TOKEN"
