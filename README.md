# TRABALHO 01:  Título do Trabalho
Trabalho desenvolvido durante a disciplina de Banco de dados

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
primeiro_componente_do_grupo:fellipywagmacker123@gmail.com<br>
segundo_componente_do_grupo:dara.botecchia22@gmail.com<br>
terceiro_componente_do_grupo:evelynpo59@gmail.com<br>

### 2.INTRODUÇÃO E MOTIVAÇÃO<br>
Este documento contém a especificação do projeto do banco de dados <nome do projeto> 
<br>e motivação da escolha realizada. <br>

> A loja visa colaborar com o desenvolvimento socioprofissional dos seus colaboradores e acima da venda de produtos, entregar experiências diferenciadas para o seu público alvo. O sistema da loja tem como objetivo gerenciar todos os processos da organização, bem como controlar e gerar relatórios analíticos. Para que seja efetuado tal gerenciamento é realizado o cadastro de  pessoa física como por exemplo: cliente, funcionário, compra, produto e Pessoa jurídica: loja, fornecedores, compra, produto. De acordo com o gerenciamento nada sai e entra da loja sem que seja processado pelo sistema, desde mercadorias, valores, impostos, folhas de pagamento, aquisição de bens, investimentos, receita e despesas. O sistema promove uma gestão mais assertiva e confiável.
 

### 3.MINI-MUNDO<br>

Descrever o mini-mundo! (Não deve ser maior do que 30 linhas, se necessário resumir para justar) <br>
Entrevista com o usuário e identificação dos requisitos.(quando for o caso de sistemas com cliente  real)<br>
Descrição textual das regras de negócio definidas como um  subconjunto do mundo real 
cujos elementos são propriedades que desejamos incluir, processar, armazenar, 
gerenciar, atualizar, e que descrevem a proposta/solução a ser desenvolvida.

> Um sistema gerencia várias LOJAS, para uma melhor organização foram distribuídos dados de PESSOA FISICA e PESSOA JURIDICA. Portanto, em PESSOA FISICA foram armazenados as informações das seguintes entidades: CLIENTE ( codigo, nome, cpf, telefone), FUNCIONARIO ( codigo, nome, cpf, rg, data_de_contratacao, telefone), associados ao o relacionamento COMPRA ( data_hora_compra, quantidade) e conectado a entidade PRODUTO( marca, preco, codigo). Portanto, um cliente pode comprar um ou vários produtos e o funcionário pode vender um ou vários produtos para os clientes. Seguimos agora com as informações armazenadas em PESSOA JURIDICA com as seguintes entidades: LOJA ( CNPJ, nome, telefone, email), FORNECEDOR (CNPJ, nome_transportadora, endereço, telefone), associados ao o relacionamento FORNECER ( data_hora_compra, forma_de_pagamento, quantidade) e conectado a entidade PRODUTO( marca, preco, codigo). Sendo assim, uma loja pode ter um ou vários fornecedores e os fornecedores podem fornecer para uma ou várias lojas, podendo comprar um ou vários produtos. 

   

### 4.PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    a) O sistema proposto poderá fornecer quais tipos de relatórios e informaçes? 
    
    Além de gerenciar todos os processos realizados na empresa o sistema irá gerar relatórios analíticos, trazendo informações  de Pessoa física, Pessoa jurídica, dados de seus produtos e informações sobre vendas realizadas. Portanto, o sistema proposto contribui com a organização e armazenagem de informações da empresa.
    
    b) Crie uma lista com os 5 principais relatórios que poderão ser obtidos por meio do sistema proposto!
    
. Pessoa, sendo ela física ou jurídica.<br>
. Loja: CNPJ, nome, telefone, email.<br>
. Dados de seus funcionários: Código, nome, cpf, data de contratação, telefone.<br>
. Informações de seus fornecedores: CNPJ, nome da transportadora, endereço, telefone.<br>
. Relatórios de vendas realizadas pelas lojas: Data e hora da compra, forma de pagamento, produto.<br>

    

 ### 5.MODELO CONCEITUAL<br>
       
![Alt text](Conceitual_grupo.png "Modelo Conceitual")
    
       
#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: [ ]
    [Grupo02]: [ ]

#### 5.2 Descrição dos dados 
    
Pessoa: Entidade na qual contém uma associação entre Pessoa Física e Pessoa Jurídica.<br>
Pessoa Física: Inclui informações sobre cliente e funcionário. <br>
Pessoa Jurídica: Inclui informações sobre Loja e Fornecedor.<br>
Cliente: Campo que abrange dados sobre os clientes cadastrados.<br>
Funcionário: Campo que abrange dados sobre os funcionários.<br>
Compra: Contém dados sobre as compras realizadas.<br>
Produto: Dados sobre os produtos.<br>
Loja: Inclui informações sobre a loja.<br>
Fornecedor: Campo que armazena informações sobre os fornecedores.<br>

### 6 MODELO LÓGICO<br>

![Alt text](Lógico_grupo.png "Modelo Lógico")

### 7 MODELO FÍSICO<br>
	
CREATE TABLE PESSOA(
codigo integer,
nome varchar(80)
);

--------------------------------------------------------------------------------------------------------------------------------------------------------
	
CREATE TABLE LOJA(
cnpj integer PRIMARY KEY,
nome varchar(150),
telefone integer,
email varchar(150)
);
  
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
CREATE TABLE FORNECEDOR(
cnpj integer PRIMARY KEY,
nome_transportadora varchar(100),
telefone integer,
cep integer,
numero integer,
rua varchar(25),
bairro varchar(30)
);
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
CREATE TABLE FUNCIONARIO(
codigo integer PRIMARY KEY,
nome varchar(170),
cpf integer,
rg integer,
data_contratacao date,
telefone integer
);

--------------------------------------------------------------------------------------------------------------------------------------------------------
	
CREATE TABLE CLIENTE(
codigo integer PRIMARY KEY,
nome varchar(80),
cpf integer,
telefone integer
)
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
CREATE TABLE PRODUTO(
codigo integer PRIMARY KEY,
marca varchar(70),
preco float
);
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
CREATE TABLE LOJA_FORNECEDOR(
FK_LOJA_cnpj integer,
FK_FORNECEDOR_cnpj integer,
FK_PRODUTO_codigo integer,
data_hora_compra timestamp,
forma_de_pagamento varchar(20),
qtd integer,

FOREIGN KEY(FK_LOJA_cnpj)
REFERENCES LOJA(cnpj),
FOREIGN KEY(FK_FORNECEDOR_cnpj)
REFERENCES FORNECEDOR(cnpj),
FOREIGN KEY(FK_PRODUTO_codigo)
REFERENCES PRODUTO(codigo)
);
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
CREATE TABLE CLIENTE_FUNCIONARIO(
FK_FUNCIONARIO_codigo integer,
FK_CLIENTE_codigo integer,
FK_PRODUTO_codigo integer,
forma_de_pagamento varchar(20),
qtd integer,

FOREIGN KEY (FK_FUNCIONARIO_codigo)
REFERENCES FUNCIONARIO(codigo),
FOREIGN KEY (FK_CLIENTE_codigo)
REFERENCES CLIENTE(codigo),
FOREIGN KEY (FK_PRODUTO_codigo)
REFERENCES PRODUTO(codigo)
);

       
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
INSERT INTO PESSOA(codigo, nome)
VALUES(010101, 'Iago Oliveira'),
      (020202, 'Luiz Henrique'),
      (030303, 'Julia Cardoso'),
      (040404, 'Lionel Messi'),
      (050505, 'Arthur Fernandes'),
      (060606, 'Maikon da Silva'),
      (070707, 'Ana Julia'),
      (080808, 'Vanessa de Alcantra');
	
SELECT * FROM PESSOA;
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
INSERT INTO LOJA(cnpj, nome, telefone, email)
VALUES(833898, 'Gucci', 31990400, 'roupasgucci@gmail.com'),
      (10401257, 'Zazzle', 35771747, 'confeczazzle@gmail.com'),
      (39752353, 'Sacudidos', 37221828, 'sacudidos@gmail.com'),
      (71354641, 'Reserva', 35502024, 'reserva@gmail.com'),
      (36226675, 'Nike', 27396558, 'nikebr@gmail.com'),
      (42274696, 'Adidas', 21966400, 'adidasbr@gmail.com'),
      (2799216, 'COWBOY STORE', 85950000, 'cowboystore@gmail.com'),
      (29511391, 'Lacoste', 20090000, 'lascostebr@gmail.com');
 
SELECT * FROM LOJA;
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
INSERT INTO FORNECEDOR(cnpj, nome_transportadora, telefone, cep, numero, rua, bairro)
VALUES(65126600, 'TRANSPORTADORA TRESSI', 30530314, 85906370, 151, 'Avenida Jose Joao Muraro', 'JARDIM PORTO ALEGRE'),
   (41040017, 'DELLMAR TRANSPORTES', 30123636, 29136519, 432, 'Rua Idalino Carvalho', 'PARQUE INDUSTRIAL'),
      (48766012, 'ATLAS', 21017300, 95110690, 323, 'Rodovia Rst', 'DESVIO RIZZO'),
      (11080089, 'ALFA TRANSPORTES EIRELI', 35615100, 13178440, 098, 'Rodovia Adauto Campo', 'JARDIM MANCHESTER'),
      (24617014, 'JAMEF TRANSPORTES', 21028803, 32210130, 181, 'Rua Doutor Jose Americo', 'CIDADE INDUSTRIAL'),
      (43603530, 'PATRUS TRANSPORTES', 21911000, 38706215, 308, 'Avenida Juscelino', 'RESIDENCIAL GRAMADO'),
      (74031027, 'BRASPRESS TRANSPORTES', 21889000, 81350100, 643, 'Rua Joao Bettega', 'CIDADE INDUSTRIAL'),
      (59171699, 'TNT CARGAS', 30402900, 64224749, 432, 'Rodovia Washington', 'VILA SAO LUIZ');
SELECT * FROM FORNECEDOR;
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
INSERT INTO FUNCIONARIO(codigo, nome, cpf, rg, data_contratacao, telefone)
VALUES(593485, 'Fellipy Wagmacker', 31871588, 1640575, '2022-01-09', 26314646),
      (982521, 'Dara Mendes Botecchia', 83600546, 3578845, '2019-07-21', 23079480),
      (148284, 'Evelyn Pereira Otavio', 03899287, 7373073, '2022-09-12', 27282770),
      (324988, 'Iara Da Silva Menezes Mendes Botecchia', 24840415, 5766963, '2011-09-22', 35580223),
      (765546, 'Jussara Da Silva Wagmacker Galdino', 60565825, 2854453, '2020-10-22', 20608710),
      (135824, 'Evaldo Silva de Oliveira', 28871120, 5373658, '2010-01-11', 36786343),
      (863633, 'Lucas Lomenge', 75019300, 0611457, '2022-11-20', 23335875),
      (764343, 'Davi Mendes Botecchia', 80916677, 2404596, '2019-11-21', 37114971);

SELECT * FROM FUNCIONARIO;
	
--------------------------------------------------------------------------------------------------------------------------------------------------------	
	
INSERT INTO CLIENTE(codigo, nome, cpf, telefone)
VALUES(01001, 'Vanderlei da Cunha', 509352042, 30136375),
     (02002, 'Robson da Silva', 880417080, 36438677),
     (03003, 'Roni de Oliveira', 327138076, 21830055),
     (04004, 'Cleide Nascimento', 389772052, 24836835),
     (05005, 'Seu zé da Conceição', 844307051, 29148601),
     (06006, 'Maria Clara', 844397051, 23111732),
     (07007, 'Roberta Galdino', 354989033, 28717025),
     (08008, 'Vitoria Campos', 116858079, 22881293);
 
SELECT * FROM CLIENTE;
	
--------------------------------------------------------------------------------------------------------------------------------------------------------

INSERT INTO PRODUTO(codigo, marca, preco) 
VALUES(070777, 'Nike', 79.99), 
      (090999, 'Adidas', 129.99), 
      (040444,'Reserva', 99.99), 
      (020222, 'Nike', 55.50), 
      (056056, 'Nike', 100.50), 
      (027027, 'Zazzle', 349.99), 
      (010111, 'Zazzle', 259.99), 
      (080888, 'Nike', 199.99);

SELECT * FROM PRODUTO;
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
INSERT INTO loja_fornecedor(FK_FORNECEDOR_cnpj, FK_LOJA_cnpj, FK_PRODUTO_codigo, data_hora_compra, forma_de_pagamento, qtd)
VALUES(11080089, 833898, 040444,'2020-09-09 13:45:55', 'Cartão', 1500),
      (65126600, 29511391, 070777,'2022-12-15 17:09:21', 'Cartão', 500),
      (43603530, 39752353, 027027,'2022-01-29 09:30:30', 'Cartão', 90),
      (74031027, 36226675, 010111,'2013-07-17 18:59:59', 'Dinheiro', 200),
      (59171699, 71354641, 056056,'2018-06-05 22:10:44', 'Cartão', 450),
      (24617014, 42274696, 080888,'2016-04-30 16:47:12', 'Dinheiro', 1200),
      (48766012, 2799216, 020222,'2019-03-19 18:30:31', 'Dinheiro', 60),
      (41040017, 10401257, 090999,'2015-08-31 14:58:01', 'Cartão', 1150);

SELECT * FROM loja_fornecedor;
	
--------------------------------------------------------------------------------------------------------------------------------------------------------
	
INSERT INTO CLIENTE_FUNCIONARIO(FK_FUNCIONARIO_codigo, FK_CLIENTE_codigo, FK_PRODUTO_codigo, forma_de_pagamento, qtd)
VALUES(148284, 07007, 027027, 'Cartão', 2),
     (324988, 04004, 070777, 'Cartão', 1),
 (764343, 06006, 010111, 'Dinheiro', 1),
 (135824, 01001, 040444, 'Dinheiro', 1),
 (593485, 08008, 020222, 'Dinheiro', 2),
 (765546, 03003, 080888, 'Cartão', 2),
 (863633, 05005, 090999, 'Dinheiro', 3),
 (982521, 06006, 056056, 'Cartão', 3);
SELECT * FROM CLIENTE_FUNCIONARIO;	
	

### 9	TABELAS E PRINCIPAIS CONSULTAS<br>

TABELA PESSOA<br>
       
![Alt text](TABELA_PESSOA.png "Tabela Pessoa")<br>
	
--------------------------------------------------------------------------------------------------------------------------------------------------------------
	
TABELA LOJA<br>
       
![Alt text](TABELA_LOJA.png "Tabela Loja")<br>
	
--------------------------------------------------------------------------------------------------------------------------------------------------------------
	
TABELA FORNECEDOR<br>
       
![Alt text](TABELA_FORNECEDOR.png "Tabela Fornecedor")<br>
	
--------------------------------------------------------------------------------------------------------------------------------------------------------------

TABELA LOJA_FORNECEDOR<br>
       
![Alt text](TABELA_LOJA_FORNECEDOR.png "Tabela Loja_Fornecedor")<br>	
	
--------------------------------------------------------------------------------------------------------------------------------------------------------------	
TABELA CLIENTE<br>
       
![Alt text](TABELA_CLIENTE.png "Tabela Cliente")<br>
	
--------------------------------------------------------------------------------------------------------------------------------------------------------------
	
TABELA FUNCIONARIO<br>
       
![Alt text](TABELA_FUNCIONARIO.png "Tabela Funcionario")<br>]
	
--------------------------------------------------------------------------------------------------------------------------------------------------------------
	
TABELA CLIENTE_FUNCIONARIO<br>
       
![Alt text](TABELA_CLIENTE_FUNCIONARIO.png "Tabela Cliente_Funcionario")<br>
	
	
	
	

># Marco de Entrega 01: Do item 1 até o item 9.1<br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>

SELECT * FROM FUNCIONARIO WHERE data_contratacao >= '2019-09-22';<br>

SELECT * FROM CLIENTE_FUNCIONARIO WHERE forma_de_pagamento = 'Cartão';<br>

SELECT * FROM LOJA_FORNECEDOR WHERE forma_de_pagamento = 'Dinheiro' and qtd > 90;<br>

SELECT * FROM PRODUTO where marca = 'Adidas' or preco < 150.00;<br>

SELECT * FROM CLIENTE WHERE codigo < 6006 and nome like '%de%';
#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    b) Criar no mínimo 3 consultas com operadores aritméticos 
    c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    b) Criar uma consulta para cada tipo de função data apresentada.

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão
    b) Criar minimo 3 de atualização

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado
    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
     a) Criar minimo 1 envolvendo GROUP BY
     b) Criar minimo 1 envolvendo algum tipo de junção

># Marco de Entrega 02: Do item 9.2 até o ítem 9.10<br>

### 10 RELATÓRIOS E GRÁFICOS (Usar template disponibilizado)
[Template de relatórios](https://github.com/discipbdint/public_samples/blob/main/BD_Exemplo_Relatorios_Empresa_VA.ipynb "Template relatórios")

#### a) análises e resultados provenientes do banco de dados desenvolvido (usar modelo disponível)
#### b) link com exemplo de relatórios será disponiblizado pelo professor no AVA
#### OBS: Esta é uma atividade de grande relevância no contexto do trabalho. Mantenha o foco nos 5 principais relatórios/resultados visando obter o melhor resultado possível.

    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>

#### a) Modelo (pecha kucha)<br>
#### b) Tempo de apresentação 6:40 

># Marco de Entrega 03: Itens 10 e 11<br>
<br>
<br>
<br> 



### 12 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://www.sis4.com/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")


