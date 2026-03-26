```python
cat > b.py <<'EOF'
from azure.identity import DefaultAzureCredential
from azure.storage.blob import BlobServiceClient
import os

account_url = "https://scgptuksouthdevchatgptul.blob.core.windows.net/"
container_name = "data"

# 要下载的“文件夹”
blob_prefix = "abc/"

# 本地保存根目录
local_root = "abc"

credential = DefaultAzureCredential()
blob_service_client = BlobServiceClient(account_url=account_url, credential=credential)
container_client = blob_service_client.get_container_client(container_name)

print(f"开始列出并下载前缀为 {blob_prefix!r} 的 blobs ...")

found = False
for blob in container_client.list_blobs(name_starts_with=blob_prefix):
    found = True
    blob_name = blob.name

    # 例如 abc/x/y.txt -> 本地 abc/x/y.txt
    relative_path = blob_name[len(blob_prefix):]
    if not relative_path:
        continue

    local_file = os.path.join(local_root, relative_path)
    local_dir = os.path.dirname(local_file)
    if local_dir:
        os.makedirs(local_dir, exist_ok=True)

    print(f"下载: {blob_name} -> {local_file}")
    blob_client = container_client.get_blob_client(blob_name)
    with open(local_file, "wb") as f:
        download_stream = blob_client.download_blob()
        f.write(download_stream.readall())

if not found:
    print(f"没有找到前缀为 {blob_prefix!r} 的 blob")
else:
    print(f"下载完成，本地目录: {os.path.abspath(local_root)}")
EOF
EOF
