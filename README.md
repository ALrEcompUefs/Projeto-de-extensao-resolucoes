<h1> Projeto de extensão </h1>
<p>Repositório para o projeto de extensão da disciplina EXA 844 Programação para redes da Universidade Estadual de Feira de Santana (UEFS)</p>

<h3>Resumo do projeto</h3>

<p>O projeto consiste no desenvolvimento de um engenho de busca para resoluções da UEFS, o sistema deve permite o cadastro de resoluções, busca de resoluções por ano , tipo, texto e etc.</p>
<h3>Sobre o projeto</h3>

<p>O projeto é dividido em quatro módulos individuais são eles: gerenciamento de usuários , armazenamento de dados, sistema de busca e módulo de extração de dados, a fim de que os módulos fossem desenvolvidos independentes um dos outros foi estabelecido que a comunicação entre módulos seria feita através de APIs construídas junto aos módulos.</p>

<h4>Links de referência</h4>

<ul>
<a href="https://sites.google.com/a/ecomp.uefs.br/joao/home/courses/exa844"><li>Site da discplina</li><a>
<li><a href="https://www.uefs.br/modules/conteudo/conteudo.php?conteudo=146">Pagína com resoluções</a></li>
</ul>

<hr>

<h2>Módulos</h2>

<h3>Gerenciamento de usuários </h3>
<p>O módulo de gerenciamento de usuários é responsável pelo cadastro e controle de usuários, existem dois tipos de usuários administrador e usuário, Administradores tem a função do controle de usuários no sistema enquanto usuários podem cadastrar resoluções e alterar seus dados cadastrais.</p>

<p>Funcionalidades do Administrador:</p>
<ul>
    <li>Cadastrar/Remover usuários</li>
    <li>Alterar senha dos usuários</li>
    <li>Acesso ao Log do sistema</li>
    <li>Listar usuários</li>
</ul>
<p>Funcionalidades do usuario:</p>
<ul>
    <li>Cadastrar resoluções (permissão)</li>
    <li>Alterar email e senha</li>
    <li></li>
    <li></li>
</ul>
<p>Funcionalidades do sistema:</p>
<ul>
    <li>Gerar Token de autenticação do usuário </li>
    <li>Verificar login do usuário </li>
    <li>Informação de cadastro de usuário: nome , email e senha</li>
</ul>

<h3>Extração de dados</h3>
<p>O módulo de extração de dados fica responsável pela extração dos dados das resoluções, o sistema acessa as resoluções em formato pdf faz a extração de dados e armazena no esquema estruturado definido para o projeto, algumas resoluções vão ser pdfs de documentos digitalizados sendo necessário utilizar Optical Character Recognition (OCR) para extrair os dados, o sistema deve gerar um json( no formato definido pelo projeto) para atender as requisições feitas na API construída. </p>

<p>Funcionalidades do sistema:</p>
<ul>
    <li>Acessa o armazenamento de resoluções e faz a extração dos dadas de cada resolução uma a uma.</li>
    <li>Função definida: recebe como parâmetro um arquivo pdf e retorna um json de resposta com os dados do pdf.</li>
    <li>O formato do json segue o padrão definido no arquivo: esquema_dados_modulo_extracao.json na pasta modelos.</li>
</ul>