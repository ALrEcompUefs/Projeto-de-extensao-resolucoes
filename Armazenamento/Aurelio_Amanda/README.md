# ✅ Módulo de Armazenamento
## API para efetuar o cadastro e armazenamento de resoluções da Universidade Estadual de Feira de Santana.



Índice
=================
<!--ts-->
   * [Sobre](#sobre)
   * [Equipe de Desenvolvimento](#equipe-de-desenvolvimento)
   * [Tecnologias](#tecnologias)
   * [Solução](#solucao)
   * [Consumindo API Online](#online)
   * [Executando Aplicação Localmente](#local)
<!--te-->
<div id="sobre">
    <h1> 📝 Sobre o projeto</h1>
    <p align="justify">
    O projeto proposto pela disciplina <b><a href="https://sites.google.com/a/ecomp.uefs.br/joao/home/courses/exa844">EXA 844 - Programação para redes</a></b> trata-se projeto de extensão que envolve toda a turma a desenvolver um sistema que cadastre e disponha resoluções da UEFS. 
    </p>
</div>

<div id="equipe-de-desenvolvimento">    
    <h1>👨‍💻 Equipe de Desenvolvimento</h1>
    <ul>
	<li><a href="https://github.com/aureliobarreto"> Aurélio Rocha Barreto </a></li>
    <li><a href="https://github.com/amandassa"> Amanda Silva Santos </a> </li>
	</ul>
    <h3>Professor</h3>
    <ul>
        <li><a href="https://sites.google.com/a/ecomp.uefs.br/joao/home">João Batista Rocha Junior</a></li>
    </ul>
</div>

<div id="solucao">
    <h1>💡 Solução</h1>
    <h3>API (Application Program Interface)</h3>
    <p align="justify">
 A api foi desenvolvida em Javascript com o framework Express JS, que foi hospedada na plataforma gratuita <a href="https://render.com/">Render</a>. O link da API está disponível em: <br/><b>URL:   <a href="https://dbr-engenho-de-busca.onrender.com"> https://dbr-engenho-de-busca.onrender.com </a>
    </p>
    <h3>Banco de Dados (Database)</h3>
    <p align="justify">
        O banco de dados que foi delegado para a nossa equipe foi o banco de dados relacional, dessa forma, decidimos utilizar o banco de dados Mysql, e também foi hospedado em solução gratuita pela plataforma <a href="https://aiven.io/">Aiven</a>. 
        
O banco de dados é comporto por 3 tabelas:
<ul>
<li> resolucoes</li>
</ul>

Em Resoluções estão disponíveis as colunas referentes as informações básicas da resolução
como ano, numero, reitor, data, data de inserção, texto, link, cabeçalho e email do usuário que cadastrou a resolução.

Além disso, contém uma coluna wd que é calculada para que o módulo do algoritmo de busca 
utilize para seus calculos:


<b>Cálculo do WD: 

<img src="https://github.com/amandassa/DBR-engenho-de-busca/blob/master/imgs/eq.png" alt="Equation">
 <ul>
<li> termos</li>
</ul>

em termos estão disponíveis cada termo que foi tokenizado pela API, cada termo tem seu próprio ID e cada termo é único, ou seja, não é possível ter termos duplicados.

<ul>
<li> documentos</li>
</ul>

Um documento diz respeito a um termo específico presente em uma resolução e qual frequência ele aparece nessa resolução

<b>Diagrama de Relacionamentos do Banco

<img alt="Diagrama de Relacionamentos" src="https://github.com/amandassa/DBR-engenho-de-busca/blob/master/imgs/diagrama.png"/>
    
</div>



<div id="tecnologias">
    <h1>🛠 Tecnologias </h1>
    <p>As seguintes tecnologias e ferramentas foram usadas na construção do projeto:</p>
    <ul>
        <li><a href="https://nodejs.org/">Node.js</a></li>
        <li><a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript">Javascript</a></li>
        <li><a href="https://expressjs.com/pt-br/">Express.js</a></li>
        <li><a href="https://www.mysql.com/">MySQL</a></li>
    </ul>
</div>

<div id="online">
    <h1> 🌐 Usando Solução Online </h1>
    <p  align="justify"> Para conseguir cadastrar resoluções com com a API online, siga os      seguintes passos: </p>
</div>

```bash
# Faça uma requisição http do tipo POST na rota /cadastrarResolucao 
# https://dbr-engenho-de-busca.onrender.com/cadastrarResolucao
# no body da sua requisição deverá ser passado um JSON no seguinte formato:
{
	"numero":"001/2016",
	"ano":2016,
	"data":"08/01/2016",
	"reitor":"Nome do reitor",
	"cabecalho":"todo texto até a palavra resolve",
	"texto":" todo texto da resolução",
	"link":"Link de acesso para o pdf da resolução",
    "email_usuario":"email do usuario que cadastrou a resolução"
}

**OBS**: Não envie JSON com a sintaxe errada pelo amor de DEUS!!
```
<p> <b>Respostas HTTP </b> </p>

<ul>
<li>Status 201 <span style="color: green">sucesso</span>  - Resolução cadastrada com sucesso </li>
<li>Status 400 <span style="color: red">error</span>  - Parâmetros do JSON são vazios ou incompleto</li>
<li>Status 409  <span style="color: red">error</span> - Resolução já existente no banco de dados </li>
<li>Status 500  <span style="color: red">error</span> - Erro interno no servidor </li>
</ul>

</div>

<div>
<h1> 💻 Executando a API localmente </h1>

<div id="local">
<h4>Para executar a API localmente primeiro certifique-se de ter o Nodejs e o Git instalado em sua máquina. Caso esteja tudo ok, siga os seguintes passos:</h4>

<h4>Configuração<h4>

 ```bash
$ git clone https://github.com/amandassa/DBR-engenho-de-busca.git
# Dentro da pasta onde clonou o projeto execute
$ npm install
# Crie um arquivo chamado .env na raiz do projeto para utilizar as credenciais
# do seu banco de dados
# O arquivo .env deverá as seguintes variáveis de ambiente
DB_HOST=host do banco de dados (ex: localhost)
DB_USER=usuario da database (ex: root)
DB_PORT= porta no qual seu banco de dados se encontra (ex: porta padrão 3306)
DB_PASSWORD= sua senha de usuário
DB_DATABASE= nome da database (ex: resolucoesuefsdb)

 ```
 
 <h4>Povoando o Banco de Dados <h4>

 ```bash
# Em seu banco de dados execute o script Mysql disponível no arquivo:
```
<a href="https://github.com/amandassa/DBR-engenho-de-busca/blob/master/ResolucoesUefs.sql">ResolucoesUefs.sql</a>
<h4>Executando a API<h4>

 ```bash
$ npm run dev (desenvolvimento)
$ npm start (produção)
```
