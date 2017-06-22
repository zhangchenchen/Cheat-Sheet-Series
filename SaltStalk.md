# SaltStalk Cheat Sheet

## Minions Authentication

- salt-key  -L                  # list all public keys
- salt-key  -a <PUB-KEY>        # accept the specified public key
- salt-key  -A                  # accept all public key
- salt-key  -d <PUB-KEY>        # delete the specified public key
- salt-key  -D                  # delete all public key

```bash
salt-key  -L                  # list all public keys
salt-key  -a <PUB-KEY>        # accept the specified public key
salt-key  -A                  # accept all public key
salt-key  -d <PUB-KEY>        # delete the specified public key
salt-key  -D                  # delete all public key
```