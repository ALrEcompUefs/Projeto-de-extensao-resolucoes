# ✅ Módulo de Armazenamento em um banco não relacional
## armazenamento de resoluções da Universidade Estadual de Feira de Santana.


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
	<li><a href="https://github.com/Marianasls"> Mariana Santos </a></li>
    <li><a href="https://github.com/WilliamOSoares"> William Soares </a> </li>
	</ul>
    <h3>Professor</h3>
    <ul>
        <li><a href="https://sites.google.com/a/ecomp.uefs.br/joao/home">João Batista Rocha Junior</a></li>
    </ul>
</div>

<div id="solucao">
    <h1>💡 Solução</h1>
    <h3>Application Program Interface (API)</h3>
    <p align="justify">
 A API não foi desenvolvida por conta do tempo, mas o ambiente do Atlas promove a infraestrutura necessária para implementar uma usando a linguagem JavaScript. Contudo, os códigos base já estão prontos para ajudar no desenvolvimento, mas está em Python no <a href="https://github.com/WilliamOSoares/exa844/tree/main/Projeto%20de%20Extens%C3%A3o">repositório</a>.
    </p>
    <h3>Banco de Dados (Database)</h3>
    <p align="justify">
        O banco de dados que foi delegado para a nossa equipe foi o banco de dados não relacional, dessa forma, decidimos utilizar o <a href="https://www.mongodb.com/atlas/database">Atlas database</a> do MongoDB. 
        
O banco de dados é comporto por 2 tabelas:
<ul>
<li> documentos</li>
</ul>

```bash
# formato do Json para inserção contendo as chaves da collection:
docTest = {
    'ID': '2016#002', #Será construido com ano#numero
    'numero': '003',
    'ano': '2016',
    'data': '13:06:2016',
    'reitor': 'Evandro',
    'cabecalho': 'Um teste',
    'texto': 'Isso é só um teste',
    'link': 'uefs.br',
    'cadastro': time.strftime('%d-%m-%Y'),
    'user': 'joao@uefs.br',
    'wd': '4.341' #Será calculado pela API
}
```

<li> termos</li>
</ul>

```bash
# formato do Json para inserção contendo as chaves da collection:
termoTest = {
    'palavra': 'Isso',
    'lista': [('2016#003',1)]
}
```
OBS: As soluções precisam ser mais desenvolvidas para serem integradas com outros módulos de códigos, devido ao tempo não foi gerado tudo que era necessário, ou seja, faltou a adição dos dados ft(quantidade de documentos que contém a palavra), Ft (quantidade total de repetição da palavra em todos os documentos), n (quantidade de termos na coleção) e N (quantidade de documentos na coleção).

    
</div>



<div id="tecnologias">
    <h1>🛠 Tecnologias </h1>
    <p>As seguintes tecnologias e ferramentas foram usadas na construção do projeto:</p>
    <ul>
        <li><a href="https://api.mongodb.com/python/3.3.1/tutorial.html">pymongo</a></li>
        <li><a href="https://www.w3schools.com/js/default.asp">javascript</a></li>
        <li><a href="https://www.w3schools.com/python/default.asp">python</a></li>
    </ul>
</div>

<div id="online">
    <h1> 🌐 Usando Solução e Executando no desktop 💻 </h1>
    <p  criando a database no Atlas com os seguintes passos: </p>
</div>

<p> <b>Respostas HTTP </b> </p>

<ul>
<li>Acesse e faça o login: <a href=""https://account.mongodb.com/account/login""> Atlas database</a> </li>
<li>Crie um projeto e dê um nome e faça uma senha simples</li>
<li>Vá em Database, click em Creat-> Shared-> GoogleCloud-> southamerica-east1-> M0 Sandbox-> e coloque um nome </li>
<li>Vá em Network Access, click em Add IP address-> Coloque seu IP-> Coloque uma identificação-> Confirm </li>
<li>Aproveite e insira o IP 0.0.0.0 </li>
<li>Volte para Database, click em Connect-> Drivers-> Escolha o Driver(linguagem de programação)-> Escolha a versão-> Habilite View full code sample-> copie o código</li>
<li>No código você tem que alterar a string uri colocando a senha da seu projeto no lugar do <password></li>
<li>Depois disso pode fazer a conexão com o banco para ver se deu tudo certo</li>
<li>Para criar tabela vá em Browse Collections-> Create Database-> Escolha um nome para a base-> Escolha um nome para a tabela-> coloque Capped Collection-> Coloque o tamanho em bytes da sua tabela </li>
<li>Agora no código de conexão é possivel acessar a tabela e fazer CRUD nela </li>
</ul>

</div>

 <h4>Fim ¯\_(ツ)_/¯<h4>
