1. Enable **System Managed Identity** on both **App service** and **Function App**
2. Save Generated Principal IDs for future reference
3. Head over to `partsunlimited-kv-{uniquesuffix}`, open **Access Policies** and grant yourself permissions to manage secrets
3. Create new Secret in **Key Vault**, call it `DbConnectionString` and paste DB connection string here
4. Head over to **Access Policies** and click **+ Add Access Policy**. Pick `Secret Management` template 
5. Select **App Service** principal by ID from step 2
6. Repeat steps 4-5 for principal ID of **Function App**
7. Head over to App Service and update `DefaultConnectionString` to `@Microsoft.KeyVault(VaultName=partsunlimited-kv-{uniquesuffix};SecretName=DbConnectionString)`
8. Save and observe green tick in the Source column
9. Head over to **Function App** and replace connection string with KV reference there