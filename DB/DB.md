create table categorias(
id_categoria integer not null AUTO_INCREMENT PRIMARY KEY,
nome_categoria varchar(100),
descricao varchar(255),
status varchar(20)
);

create table equipes(
id_equipe integer not null AUTO_INCREMENT PRIMARY KEY,
nome_equipe varchar(100),
area_atuacao varchar(100),
data_criacao date
);

create table tarefas(
id_tarefas integer not null AUTO_INCREMENT PRIMARY KEY,
titulo varchar(100),
descricao text,
prazo date
);

create table funcionarios(
id_funcionario integer not null AUTO_INCREMENT PRIMARY KEY,
nome_funcionario varchar(100),
cargo varchar(60),
id_equipe integer,
foreign key(id_equipe) references equipes(id_equipe)
);

create table funcionarios_tarefas(
id_funcionario integer,
id_tarefas integer,
primary key(id_funcionario, id_tarefas),
foreign key(id_funcionario) references funcionarios(id_funcionario),
foreign key(id_tarefas) references tarefas(id_tarefas)
);

create table fornecedores(
id_fornecedor integer not null AUTO_INCREMENT PRIMARY KEY,
nome_fornecedor varchar(100),
contato varchar(100),
id_funcionario integer,
foreign key(id_funcionario) references funcionarios(id_funcionario)
);

create table vendas(
id_venda integer not null AUTO_INCREMENT PRIMARY KEY,
data_venda date,
valor_total decimal(10,2),
status varchar(20)
);

create table produtos(
id_produto integer not null AUTO_INCREMENT PRIMARY KEY,
nome_produto varchar(100),
preco decimal(10,2),
id_venda integer,
foreign key(id_venda) references vendas(id_venda)
);

create table categorias_produtos(
id_categoria integer,
id_produto integer,
primary key(id_categoria, id_produto),
foreign key(id_categoria) references categorias(id_categoria),
foreign key(id_produto) references produtos(id_produto)
);

create table produtos_fornecedores(
id_produto integer,
id_fornecedor integer,
primary key(id_produto, id_fornecedor),
foreign key(id_produto) references produtos(id_produto),
foreign key(id_fornecedor) references fornecedores(id_fornecedor)
);

create table lotes(
id_lote integer not null AUTO_INCREMENT PRIMARY KEY,
codigo_lote varchar(50),
data_validade date,
id_produto integer,
foreign key(id_produto) references produtos(id_produto)
);

create table nota_fiscal(
id_venda integer not null PRIMARY KEY,
numero_nf varchar(50),
data_emissao date,
valor_nf decimal(10,2),
foreign key(id_venda) references vendas(id_venda)
);

create table forma_de_pagamento(
id_venda integer not null PRIMARY KEY,
tipo_pagamento varchar(50),
parcelas integer,
valor_pago decimal(10,2),
foreign key(id_venda) references vendas(id_venda)
);
