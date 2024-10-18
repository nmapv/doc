# Resumo

Este documento tem como objetivo orientar na integração do SonarQube com o Azure Pipelines, detalhando o processo para configurar a execução de testes unitários e enviar os arquivos de cobertura de código e resultados de testes. Serão apresentados os passos necessários para configurar o pipeline, executar os testes e gerar relatórios nos formatos adequados para análise no SonarQube, garantindo assim uma melhor visibilidade sobre a qualidade do código e cobertura de testes.

# Dependência

Crie um projeto de teste separado e adicione a biblioteca coverlet.collector como dependência.

```dotnet add package coverlet.collector```

# Pipeline

1. Crie uma task para executar os testes unitários e gerar os arquivos necessários para a análise no `SonarQube`."

```
steps:
- task: DotNetCoreCLI@2
  displayName: Test
  inputs:
    command: test
    projects: '**/Test.csproj'
    arguments: '--logger "trx" --collect:"XPlat Code Coverage;Format=cobertura,opencover" --results-directory $(Build.SourcesDirectory)/TestResults'
```

### --logger "trx"

* O arquivo trx contém informações detalhadas sobre os testes executados, como resultados, falhas e logs, e pode ser processado por várias ferramentas de CI/CD ou análise.

### --collect:"XPlat Code Coverage;Format=cobertura,opencover"

* XPlat Code Coverage: Habilita a cobertura de código multiplataforma (XPlat, ou cross-platform), que é o componente responsável por coletar os dados de cobertura.
* Format=cobertura,opencover: Especifica os formatos de saída dos relatórios de cobertura de código. Neste caso, os formatos escolhidos são:

### --results-directory $(Build.SourcesDirectory)/TestResults

* Especifica o diretório onde os resultados dos testes, incluindo o arquivo trx e os relatórios de cobertura, serão salvos.
* $(Build.SourcesDirectory) é uma variável de ambiente do Azure DevOps Pipeline que representa o diretório raiz do código-fonte no qual o build está sendo executado. O subdiretório TestResults é onde os arquivos gerados pelos testes e cobertura serão armazenados.

2. 

