# Azure DevOps agent til docker

## Indhold
- Opsætning
- Start agent med docker
- Start agent med Docker compos
---

## Opsætning

Containeren har 3 enviroment variabler der skal sættes
|Enviroment variabel|Beskrivelse                                                         |
|-------------------|--------------------------------------------------------------------|
|AZP_URL            |Url til DevOps organitation fx. https://dev.azure.com/myorganisation|
|AZP_TOKEN          |Personal access token(PAT) [Guide til oprettelse](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-linux?view=azure-devops#authenticate-with-a-personal-access-token-pat)
|AZP_AGENT_NAME     |Navn som bliver vist i DevOps                                       |

## Start agent med docker

### Build image
```bash
docker build --tag azure_pipeline_agent:latest .
```

### Run
```bash
docker run -d \ 
-v /var/run/docker.sock:/var/run/docker.sock \
-e AZP_URL=<Azure DevOps instance> \
-e AZP_TOKEN=<PAT token> \
-e AZP_AGENT_NAME=mydockeragent
```

## Start agent med Docker compose

### Build image
```bash
docker build --tag azure_pipeline_agent:latest .
```
Sæt enviroment variablerne i docker-compose.yml filen

### Run
```
docker-compose up -d
```


