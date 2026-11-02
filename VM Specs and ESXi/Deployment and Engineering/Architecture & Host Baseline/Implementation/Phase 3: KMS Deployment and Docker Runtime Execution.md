### 1. Docker Runtime Execution
The containerized KMS server is deployed using the following execution string to map the target licensing runtime interface externally:

```bash
docker run -d \
  --name kms-server \
  --restart unless-stopped \
  -p 1688:1688 \
  mikolatero/vlmcsd
```

### 2. Validating Host Port Listeners
To confirm the local socket loop was cleanly listening for inbound volume activation handshakes, netstat and ss commands were verified:

```bash
# Verify port 1688 is listening globally on the host
netstat -tulpn | grep 1688
# OR
ss -tulpn | grep 1688
```

---

## 💻 Guest Server Activation Commands (Windows / Windows Server)

To manually force volume licensing targets or test cross-network registration flows directly from target Windows nodes, administrative PowerShell or Command Prompt terminals utilize the Volume Activation Management utility (`slmgr.vbs`).

### 1. Set the Target KMS Host Pointer
Explicitly route the local machine's activation requests directly to the dedicated KMS host network endpoint:

```run cmd from target windows VM as Administrator
slmgr.vbs /skms <KMS_SERVER_IP_OR_FQDN>:1688
```

### 2. Trigger Active Volume Handshake Authentication
Instruct the local operating system licensing framework to reach out immediately to the specified KMS provider over the network to establish its rolling 180-day token:

```cmd
slmgr.vbs /ato
```

### 3. Audit Local Activation Profile States
Verify successful authentication handshakes, next renewal timestamps, and current evaluation status parameters locally:

```cmd
slmgr.vbs /dlv
```
