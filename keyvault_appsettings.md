# Keyvault

Documentação sobre como substituir o `appsettings.json` pelo `keyvault do azure` visando maior segurança em dados sensíveis (ou não). Sendo que cada entrada no `appsettings.json` será um `segredo` no `keyvault`.

Cenário:

![image](https://github.com/nmapv/doc/assets/59609545/15062d35-169b-4a29-8832-55211b51e3b3)

# Summary

- `az cli`
- Configuração acesso `keyvault`


# az cli

O [az cli](https://learn.microsoft.com/pt-br/cli/azure/install-azure-cli) é utilizado para autenticação no `azure identity` que para neste caso será utilizado no ambiente de desenvolvimento.

Após instalação do `az cli`, digite no terminal `az login` e realize a autenticação.

# Configuração acesso `keyvault`

No recurso keyvault vá em políticas de acessos e +criar. 



