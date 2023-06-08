[LINK PARA O REPOSITÓRIO](https://github.com/KevinCerqueira/exa844-projeto-extensao "@KevinCerqueira")

# Projeto de Extensão - OCR

Componente Curricular: EXA844 - Programação para Redes

# Autores

- [Esdras Abreu](https://github.com/esdrasabreu)
- [Kevin Cerqueira](https://github.com/KevinCerqueira)

## Sumário

- [Documentação da API](#documentação-da-api)
- [Rodando a API localmente](#rodando-a-api-localmente)
- [Como realizar o deploy no Google Cloud](#como-realizar-o-deploy-no-google-cloud)

# Documentação da API

Nessa sessão iremos explicar como utilizar a API para o processamento dos PDF. Nos exemplos iremos utilizar o PDF do link `https://drive.google.com/file/d/1iCzTq0YlgFM1g3usHYvOZuU0QtZ8xyMb` e utilizarem a url da API que está em produção `https://exa844.rj.r.appspot.com/`

### Exemplo de uso no terminal:

```sh
# Irá retornar os dados extraídos do PDF
curl -X POST -H "Content-Type: application/json" -d '{"link":"https://drive.google.com/file/d/1iCzTq0YlgFM1g3usHYvOZuU0QtZ8xyMb"}' https://exa844.rj.r.appspot.com/
```

* `X POST`: Este parâmetro especifica que o método de requisição HTTP é POST.
* `H` "Content-Type: application/json": Este parâmetro adiciona um cabeçalho à requisição que indica que o corpo da requisição está em formato JSON.
* `-d '{"link":"https://drive.google.com/file/d/1iCzTq0YlgFM1g3usHYvOZuU0QtZ8xyMb"}'`: Este parâmetro especifica o corpo da requisição. No exemplo, o corpo da requisição é um objeto JSON que contém um atributo "link" com um valor de "https://drive.google.com/file/d/1iCzTq0YlgFM1g3usHYvOZuU0QtZ8xyMb" que será o PDF que o OCR irá processar.
* `https://exa844.rj.r.appspot.com/`: Esta é a URL da API para a qual a requisição POST é enviada.

### Exemplo de Uso no Postman

1. Abra o aplicativo Postman.
2. Clique no botão "+", no topo da interface, para criar uma nova guia de solicitação.
3. No campo do método de solicitação (à esquerda da barra de endereços), selecione "POST".
4. No campo de URL (barra de endereços), insira a seguinte URL:

```sh
https://exa844.rj.r.appspot.com/
```

5. Abaixo da URL, vá para a guia "Body".
6. Selecione a opção "raw" e, no menu suspenso à direita, escolha "JSON".
7. No campo de texto que aparece, insira o seguinte JSON:

```json
{
    "link": "https://drive.google.com/file/d/1iCzTq0YlgFM1g3usHYvOZuU0QtZ8xyMb"
}
```

8. Antes de enviar a solicitação, vá para a guia "Headers".
9. Adicione um novo cabeçalho com "Content-Type" como chave e "application/json" como valor.
10. Agora você está pronto para enviar sua solicitação. Clique no botão azul "Send" à direita.

# Rodando a API localmente

Este documento descreve como executar o arquivo `app.py` localizado na pasta `src` do projeto. Antes de iniciar, por favor, garanta que todas as dependências, incluindo a biblioteca Tesseract, poppler-utils e Pillow estejam corretamente instaladas em seu sistema.

## Pré-requisitos

- Python 3.7+ instalado.
- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) instalado.
- [Poppler-utils](https://poppler.freedesktop.org/) instalado.

## Passos para Instalação

### 1. Instalação das Dependências

As dependências do projeto Python são listadas no arquivo `requirements.txt`. Para instalá-las, navegue até a pasta raiz do projeto, entre na pasta `/src` no terminal e execute o seguinte comando:

```bash
pip install -r requirements.txt
```

### 2. Instalação do Tesseract

O Tesseract é uma biblioteca de OCR (Optical Character Recognition) que é usada para reconhecer texto em imagens. Para instalar o Tesseract, você pode seguir o guia de instalação oficial [aqui](https://github.com/tesseract-ocr/tesseract#installing-tesseract).

### 3. Instalação do Poppler-utils

Poppler-utils é uma suíte de utilitários para renderizar PDFs. Para instalá-lo, você pode seguir o guia de instalação oficial [aqui](https://poppler.freedesktop.org/).

## Executando o Código Python

Após a instalação de todas as dependências, você está pronto para executar o arquivo `app.py`. Navegue até a pasta `src` do projeto no terminal e execute o seguinte comando:

```bash
python app.py
```

Isso deve iniciar o script Python. Caso você encontre algum erro, verifique se todas as dependências foram corretamente instaladas.

# Como realizar o deploy no Google Cloud

Este documento descreve como implementar e executar o arquivo `app.py` na plataforma Google App Engine (GAE).

## Pré-requisitos

- Conta no Google Cloud Platform (GCP) com um projeto ativo.
- [Google Cloud SDK](https://cloud.google.com/sdk/docs/install) instalado.
- Acesso ao Terminal / Command Line Interface.
- Dockerfile configurado no diretório do projeto (está na pasta `src` e já se encontra devidamente configurado).

## Passos para Execução

### 1. Autenticação

Autentique sua sessão do SDK da Google Cloud:

```bash
gcloud auth login
```

### 2. Selecionar Projeto

Defina seu projeto GCP como o projeto atual:

```bash
gcloud config set project [YOUR_PROJECT_ID]
```

Substitua `[YOUR_PROJECT_ID]` pelo ID do seu projeto no GCP.

### 3. Preparar o App Engine

Antes de enviar seu aplicativo, você precisa preparar o App Engine. Se esta é a primeira vez que você está fazendo isso no projeto atual, você precisará do seguinte comando:

```bash
gcloud app create
```

Isso criará um novo aplicativo App Engine no seu projeto.

### 4. Enviar o Aplicativo

Agora você está pronto para enviar seu aplicativo. Navegue até a pasta do seu projeto onde o arquivo Dockerfile está localizado e execute o seguinte comando:

```bash
gcloud app deploy
```

Este comando enviará seu aplicativo para o App Engine. O Google Cloud Platform construirá uma imagem Docker a partir do seu Dockerfile, e a implementará no App Engine.

### 5. Acessar o Aplicativo

Depois que a implementação estiver concluída, você pode acessar seu aplicativo no seguinte URL:

```
https://[YOUR_PROJECT_ID].appspot.com
```

Substitua `[YOUR_PROJECT_ID]` pelo ID do seu projeto no GCP.
