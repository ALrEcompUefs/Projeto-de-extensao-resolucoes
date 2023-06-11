# OCR / Examinador PDF

[LINK REPO](https://github.com/zinhoCerqueira/ocr)
## Sobre
Este repositório contém um módulo de um projeto maior que tem como objetivo melhorar o acesso a um conjunto de documentos da Universidade Estadual de Feira de Santana.

O módulo em questão é responsável por analisar arquivos PDF e extrair informações específicas, incluindo o número da resolução, ano, data, reitor, cabeçalho, texto e o link.

## EXA844 e o projeto de extensão
EXA844 é uma disciplina optativa do curso de Engenharia de Computação da UEFS ministrada por [João Rocha](https://github.com/joaorochajr). O objetivo da disciplina é introduzir conceitos de Programação para Redes, como sistemas distribuídos, fluxo de dados, programação front-end e back-end, além de outros frameworks voltados para a programação web.

Como desafio final da disciplina, foi proposto o desenvolvimento de um mecanismo de busca para resoluções da UEFS. A parte atribuída a nós ([Gabriel Carvalho](https://github.com/GabCarvaS), [Jader Cerqueira](https://github.com/zinhoCerqueira)) consiste em um código responsável pela análise de um arquivo PDF e extração de determinados dados.

## O funcionamento do código
Foi escolhido Python para o desenvolvimento desta seção devido à sua ampla gama de bibliotecas que agilizam a resolução do problema. Para criar rapidamente uma API, utilizamos o Flask, um framework leve e fácil de usar para o desenvolvimento web, que nos fornece um conjunto básico de ferramentas para lidar com solicitações HTTP.

A extração de dados é realizada em etapas. Primeiramente, é feita a conversão dos arquivos PDF em imagens, pois o Tesseract (os verdadeiros "olhos" do sistema) requer imagens para realizar a análise de texto, em vez de arquivos PDF. Essa conversão é realizada por meio da biblioteca [pdf2img](https://pypi.org/project/pdf2image/).

Em seguida, entra em ação o [tesseract](https://pypi.org/project/pytesseract/), uma biblioteca de reconhecimento óptico de caracteres (OCR) amplamente difundida para processar e extrair texto de imagens. Quanto mais claro o texto estiver nas imagens, melhor o Tesseract retornará um texto mais coerente com a realidade. Muitas vezes, é necessário fazer um pré-processamento nas imagens antes de utilizar o Tesseract.

Por fim, a última parte do processo envolve a manipulação do texto gerado pelo Tesseract. Basicamente, o texto é capturado com base em padrões de expressões regulares (regex) e possui melhores taxas de acertos ao buscar resoluções mais recentes, devido à qualidade dos PDFs.

## Dependências
Antes de executar o projeto espera-se que já estejam instaladas as seguintes dependências.
- Poppler: É necessário ter o Poppler instalado para realizar a conversão dos PDFs, a depender da sua plataforma deve ser tomada ações diferentes. É recomendado ver os sites oficiais dos envolvidos.
  - [pdf2img](https://pypi.org/project/pdf2image/)
  - [poppler](https://poppler.freedesktop.org/)
- Tesseract: Muitas vezes o tesseract instalado por via de :
```
pip install pytesseract
```
acaba não sendo o suficiente para o funcionamento correto do próprio e se faz necessário a instalação manual do tesseract, pode ser lido sobre [aqui](https://github.com/UB-Mannheim/tesseract/wiki).
Em adição a isso, é necesário no código a seguinte linha : 
```
pytesseract.pytesseract.tesseract_cmd = 'C:\Program Files\OCR\Tesseract.exe'
```
Lembrando que esta variável deve ser direcionada para o arquivo Tesseract.exe que foi instalado previamente como foi recomendado.

## Rodando a API local

Com todo o conteúdo explicados nos tópicos anteriores fica fácil rodar a API localmente e realizar testes rápidos e funcionais pelo próprio navegador por se tratar de uma requisição get.

Clone este repositório em sua máquina local:
```
git clone https://github.com/zinhoCerqueira/ocr
```
Acesse o diretório da aplicação:
```
cd nome_do_diretorio
```
Crie um ambiente virtual e o ative.
```
python -m venv venv
venv\Scripts\activate
```
Após executar o projeto e ele estar rodando localmente na porta 5000, onde está configurada, abra seu navegador e acesse a seguinte url.
```
http://localhost:5000/processar?url=<url_do_arquivo>
```
Substitua <url_do_arquivo> pela URL do arquivo que você deseja processar e você receberá de volta um JSON com as informações referentes ao pdf.

## Possíveis melhorias
Para quem vir um dia a pegar neste código, segue algumas melhorias que possam ser viáveis neste momeento.

- Para arquivos novos talvez o uso de tesseract seja um over, provavelmente tem bibliotecas melhores que trabalhem com arquivos pdfs "reais", por exemplo você usar um CTRL + F e pesquisar uma palavra, ela será encontrada, diferente dos mais antigos que só "imagens digitalizadas" e convertidas em pdfs se faz realmente necessário o uso do tesseract, já que a tática do CTRL + F não vai funcionar.
- Para arquivos muito grande as vezes acontece de dar problema no tesseract pq fica uma imagem muito grande pra ele analisar, pode mudar o jeito que o código está escrito e procurar os itens página por página.
- Usar uma IA para analisar os textos vindos do tesseract. Os arquivos mais antigos trazem dados tendendo a ter mais erros, uma IA vai poder analisar esses dados de maneira melhor já que padrões regex certamente falhará em pegar os dados corretamente.
