# vault
All Things Hashicorp Vault

1. Install Vault on Windows with `choco install vault`.
2. Check for upgrades with `choco upgrade vault` (As of today I'm on v 1.10.3).
3. Run the command `vault` and you should get some output.
4. Start a dev vault with `vault server -dev`.
   1. Save the unseal key and root token:
   2. `Unseal Key: Rdal5+1NNiclMc7lSSs8FSR0hPY8ILTtTs9y/uJAOso=`
   3. `Root Token: hvs.enjcioC8m1zrGmV57CuaEpw9`
5. Set env vars in PowerShell:
   1. `export VAULT_ADDR="http://127.0.0.1:8200"`
6. Set vault token var:
   1. `export VAULT_TOKEN="hvs.enjcioC8m1zrGmV57CuaEpw9"`
7. Check vault status with `vault status` and you should get some output:
```
Key             Value
---             -----
Seal Type       shamir
Initialized     true
Sealed          false
Total Shares    1
Threshold       1
Version         1.10.3
Storage Type    inmem
Cluster Name    vault-cluster-94cf39dd
Cluster ID      ec5685f2-2084-1f2d-3bce-63e65a085db4
HA Enabled      false
```
8. Create a secret:
   1. `vault kv put secret/hello foo=world
   2. You should get some output
```
== Secret Path ==
secret/data/hello

======= Metadata =======
Key                Value
---                -----
created_time       2022-06-15T03:07:16.8530222Z
custom_metadata    <nil>
deletion_time      n/a
destroyed          false
version            1
```
9. Read the secret to verify with `vault kv get secret/hello`.
```
======= Metadata =======
Key                Value
---                -----
created_time       2022-06-15T03:07:16.8530222Z
custom_metadata    <nil>
deletion_time      n/a
destroyed          false
version            1

=== Data ===
Key    Value
---    -----
foo    world
```
10. Install HVAC with `pip install hvac`. HVAC is the Hashicorp Vault API Client used to communicate with the vault server.
11. See python scripts for CRUD.