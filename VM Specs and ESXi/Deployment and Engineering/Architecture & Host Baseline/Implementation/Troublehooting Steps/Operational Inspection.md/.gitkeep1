### Issue: Container Query Handshake Returns 'No such container' Error
When auditing container runtime metrics or logs, the engine throws an explicit `Error response from daemon: No such container` exception profile.
To safely audit the server's running status and view client handshake histories without causing any configuration adjustments or state changes on the Linux environment, utilize the active container identifier (`local-kms`):

### 1. View Historical Connection & Activation Requests
```bash
docker logs local-kms
```

### 2. Stream Inbound Client Activations Live
```bash
docker logs -f local-kms
```

### 3. Verify Container Runtime Health & Port Mappings
```bash
docker ps -a --filter name=local-kms
```
