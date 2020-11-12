# PIX - Testes automatizados para executar os testes de API do PIX

Projeto para automação das APIs Caixa relacionadas ao PIX

Neste projeto foi utilizado o Plugin Newman do Postman para execução de coleções por linha de comando

## Requisitos

 - Node.js
 - NPM
 - Newman

## Estrutura de diretórios e arquivos

 - collections:    Pasta que irá conter as coleções criadas via Postman
 - envs:           Pasta que irá conter o arquivo de configuração do ambiente caso exista.
 - package.json    Arquivo que possui as dependencias necessárias e os scripts de execução do Newman
 
Obs:. se atentar ao comando de test executado pelo arquivo 
"test": "newman run collections/<COLEÇÃO> -d envs/<ENVIROMENT> -n 4 --insecure --reporters cli,html,junit --reporter-junit-export reports/ --reporter-html-export reports/"

## Executando os testes



