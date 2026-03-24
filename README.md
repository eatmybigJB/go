```python
cat > b.py <<'EOF'
from azure.identity import DefaultAzureCredential
from azure.storage.blob import BlobServiceClient
import os

account_url = "https://scgptuksouthdevchatgptul.blob.core.windows.net/"
container_name = "data"
blob_name = "pii_detector/pii_rules.json"
local_file = "pii_rules.json"

credential = DefaultAzureCredential()
blob_service_client = BlobServiceClient(account_url=account_url, credential=credential)

blob_client = blob_service_client.get_blob_client(
    container=container_name,
    blob=blob_name
)

print(f"开始下载 blob: {blob_name}")
with open(local_file, "wb") as f:
    download_stream = blob_client.download_blob()
    f.write(download_stream.readall())

print(f"下载完成，文件已保存到: {os.path.abspath(local_file)}")
EOF
