---
completed_at: 2025-09-28
url: https://tryhackme.com/room/introductiontocryptops
tags:
  - intro-rooms
  - security
  - devops
cssclasses:
  - first-fit
---
## 📝 Notes

### Regulatory and Compliance Standards

Navigating the requirements of regulatory & compliance is a challenge for any organisation. Standards such as the [Payment Card Industry Data Security Standard](https://www.pcisecuritystandards.org/standards/pci-dss/) (PCI DSS), [General Data Protection Regulation](https://gdpr-info.eu/) (GDPR), and the [Health Insurance Portability and Accountability Act](https://www.cdc.gov/phlp/php/resources/health-insurance-portability-and-accountability-act-of-1996-hipaa.html) (HIPAA) outline strict guidelines for the protection of sensitive data. Adherence to these regulations is not optional but critical for organisations to avoid hefty fines and legal repercussions. In this context, effective key management is not just a security measure, but a compliance mandate.
## 🛠️ Tools Used

### HashiCorp Vault CLI usage

**Default token TTL** is 768 hours.

```bash
# Points to a HashiCorp Vault Server
export VAULT_ADDR="http(s?)://<address>:<port>" # port default: 8222

# Logs a bunch of core status details about the server
vault status

# Unseals the vault with the initial keys generated, based on the threshold
vault operator unseal <unseal_key>

# Allows logging in using the access token
vault login

# Logs useful token info like its token_accessor and TTL
vault token lookup

# Enable secrets engine at a specific path
vault secrets enable -path=<path> kv

# Creating a policy
vault policy write <policy> - <<EOF
path "<path>" {
capabilities = ["create", "read", "update", "delete", "list"]
}
EOF

# Creating a token with a specific policy
vault token create -policy=<policy>

# Store secrets 
vault kv put <key> value="<value>"
vault kv put <key> username="<username>" password="<password>"

# Access secrets
vault kv get <key>
```
## 📚 & Further Reading