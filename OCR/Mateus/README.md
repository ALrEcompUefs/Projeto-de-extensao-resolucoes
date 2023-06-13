# OCR

[LINK REPO](https://github.com/MatFSantos/ocr-python)
## Sobre
Este repositório contém API capaz de ler o conteúdo de PDF's externos de Resoluções e entregar informações pertinentes à sua análise.

### O Projeto e suas ferramentas
O projeto da API utilizou a linguagem de programação Python por conta da grande disponibilidade de recursos que suprem as suas necessidades, além também de ser de muito fácil uso. Juntamente com a linguagem de script utilizada, foi feito o uso do [Tesseract](https://github.com/tesseract-ocr/tesseract), software de reconhecimento ótico de caracteres de código aberto.

Como o Tesseract trabalha diretamente com imagens, é necessário fazer a conversão de todas as páginas do PDF analisado para arquivos de imagem e, para isso, foi utilizada uma biblioteca do Python bastante usada que é a [pdf2img](https://pypi.org/project/pdf2image/). Após essa conversão o Tesseract, por meio da biblioteca que o integra com a linguagem Python, [pytesseract](https://pypi.org/project/pytesseract/), é feito a leitura das imagens, e conversão para strings.

## Como rodar (How to use)

Para poder utilizar essa API, é necessário que tenha em sua máquina a *Engine* do Tesseract. Para fazer a instalação é simples e depende apenas do seu SO.
- Linux
    - ```sudo apt-get install tesseract -y```
- Windows
    - Basta seguir as instruções contidas [aqui](https://tesseract-ocr.github.io/tessdoc/Installation.html).

Outra dependência é necessária caso esteja em máquinas Linux, a *poppler-utils*, caso ainda não a possua:
- ```sudo apt-get install poppler-utils -y```

A versão do Python utilizada foi a 3.10, sendo assim é recomendado que seja utilizado essa ou superior, sendo mais correto utilizar a 3.10.

### Clonando repositório
Utilize o git para clonar o repositório em sua máquina.
- ```git clone https://github.com/MatFSantos/ocr-python```

A pasta raiz terá o nome de ```ocr-python/```

### Ambiente de desenvolvimento
Para encapsular o ambiente foi feito o uso do *pipenv*, ferramenta de gerenciamento de ambiente virtual do python que gere todo o seu ambiente e dependências. Para obtê-lo é simples.
- ```pip install pipenv```
    - Obs: esse método de encapsulamento não é obrigatório, podendo ser utilizado outros como o *venv*. Caso utilize o *pipenv*, é importante que a versão do Python seja a 3.10, para não gerar conflitos em suas dependências. Caso opte pelo *venv*, basta verificar no arquivo ```./PipFile``` as dependências necessárias e instalar.

Após o gerenciador de ambiente de desenvolvimento instalado, podemos instalar as dependências do projeto e entrar no ambiente. Para isso, esteja na pasta raiz do projeto.
- ```pipenv install --dev```
- ```pipenv shell```

### Executando servidor

Por fim, após todos os passos já comentados é possível subir a API na porta ```:5000```.
- ```python run.py```

A rota da API que disponibiliza a funcionalidade é feita através do método POST, sendo necessário um framework para teste de API, como Insomnia ou Postman.
- http://localhost:5000/ocr

No body da requisição é necessário mandar um parâmetro, o link do pdf que deseja extrair os dados.
```
{
    "link": "link do pdf"
}
```

## Possíveis melhorias
É importante ressaltar que o OCR projetado ainda não está 100%, tendo muitas aberturas para erros por conta da falta de padronização nas diversas Resoluções, sendo muito dificil codificar um algoritmo capaz de suprir todos os modelos.

Com isso é interessante que alguns pontos sejam mensinados aqui.
- Uma possível melhoria seria a implantação de uma IA para analisar o texto extraído do PDF e procurar pelas informações desejadas, não fazendo necessidade que um algoritmo complexo seja implementado.
- Outra melhoria seria a identificação dos PDF que são capazes de serem lidos por ferramentas mais ágeis (o Tesseract leva tempo para reconhecer os caracteres), pois atualmente todos os PDFs, até aqueles que não são digitalizados, são transformados em imagens para que seus textos sejam extraídos com o Tesseract. Isso custa tempo de processamento.
