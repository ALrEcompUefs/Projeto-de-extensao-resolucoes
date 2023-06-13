[LINK PARA O REPOSITÓRIO FRONT-END](https://github.com/silas-silva/frontend_projeto_final_redes "@silas-silva")

[LINK PARA O REPOSITÓRIO BACK-END](https://github.com/silas-silva/backend_projeto_final_redes "@silas-silva")

# Projeto de Extensão - Cadastro

Componente Curricular: EXA844 - Programação para Redes

# Autores

- [Ozenilson Cruz](https://github.com/ozenilsoncruz)
- [Silas Silva](https://github.com/silas-silva)

## Sumário

- [Como configurar Google Drive para receber arquivos](#como-configurar-o-google-drive)
- [Documentação da API](#documentação-da-api)

# Como configurar Google Drive para receber arquivos

Este documento descreve como ter acesso a conta do google drive para realizar upload de arquivos.

## Pré-requisitos

- Conta no Google Cloud Platform (GCP) com um projeto ativo.

## Passos para Execução

### 1. Tutorial de configuração

- [Upload de imagem no Google Drive com Node.Js](https://www.youtube.com/watch?v=GSHc5vlj6aQ)


# Documentação da API

Nessa sessão iremos explicar como utilizar a API para o enviar um ZIP que contém pdfs e busca as resoluções.

### Rotas:

#### Post
* "https://backendprojetofinalredes-production.up.railway.app/upload"

Essa rota recebe o arquivo zip, o ano da resolução e o tipo da resolução. EX:
```
{
  "zipFile" : file,
  "ano": 2010,
  "tipo" : "Consep"
}
```
Retorna
```
{
  [ "link para o pdf no google", "link para o pdf no google" ...] 
}
```


* "https://backendprojetofinalredes-production.up.railway.app/buscar"

Essa rota recebe os dados para fazer a busca 
```
{
  "palavrasChave" : "carga horaria", 
  "dataInicio" : 2010, 
  "dataFim" : 2015
}
```

Retorna
```
{
	"ano":"ano da resolução",
	"orgao":"orgão responsavel resolução, Consep ou Consu",
	"descricao":"resumo que descreve o assunto tratado pela resolução",
	"numero":"numero da resolução",
	"link":"Link para o pdf da resolução que permita o seu download"
}
```
