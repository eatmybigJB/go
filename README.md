```python
apiVersion: secrets-store.csi.x-k8s.io/v1
kind: SecretProviderClass
metadata:
  name: app-kv-secret
  namespace: application
spec:
  provider: azure
  secretObjects:
    - secretName: app-k8s-secret
      type: Opaque
      data:
        - objectName: my-remote-secret
          key: password
  parameters:
    usePodIdentity: "false"
    useVMManagedIdentity: "true"
    userAssignedIdentityID: "<managed-identity-client-id>"
    keyvaultName: "<your-keyvault-name>"
    tenantId: "<your-tenant-id>"
    objects: |
      array:
        - |
          objectName: my-remote-secret
          objectType: secret


apiVersion: v1
kind: Pod
metadata:
  name: secret-sync-trigger
  namespace: application
spec:
  containers:
    - name: busybox
      image: busybox:1.36
      command: ["sh", "-c", "sleep 3600"]
      volumeMounts:
        - name: secrets-store-inline
          mountPath: /mnt/secrets-store
          readOnly: true
  volumes:
    - name: secrets-store-inline
      csi:
        driver: secrets-store.csi.k8s.io
        readOnly: true
        volumeAttributes:
          secretProviderClass: app-kv-secret

kubectl get secret app-k8s-secret -n application
