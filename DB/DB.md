create table categorias(
id_categoria integer not null AUTO_INCREMENT PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
Row3 varchar(60)
);

create table equipes(
id_equipe integer not null AUTO_INCREMENT PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
Row3 varchar(60)
);

create table tarefas(
id_tarefas integer not null AUTO_INCREMENT PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
Row3 varchar(60)
);

create table funcionarios(
id_funcionario integer not null AUTO_INCREMENT PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
id_equipe integer,
foreign key(id_equipe) references equipes(id_equipe)
);

create table funcionario_tarefas(
id_funcionario integer,
id_tarefas integer,
primary key(id_funcionario, id_tarefas),
foreign key(id_funcionario) references funcionarios(id_funcionario),
foreign key(id_tarefas) references tarefas(id_tarefas)
);

create table fornecedores(
id_fornecedor integer not null AUTO_INCREMENT PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
id_funcionario integer,
foreign key(id_funcionario) references funcionarios(id_funcionario)
);

create table vendas(
id_venda integer not null AUTO_INCREMENT PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
Row3 varchar(60)
);

create table produtos(
id_produto integer not null AUTO_INCREMENT PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
id_venda integer,
foreign key(id_venda) references vendas(id_venda)
);

create table categoria_produtos(
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
Row1 varchar(60),
Row2 varchar(60),
id_produto integer,
foreign key(id_produto) references produtos(id_produto)
);

create table nota_fiscal(
id_venda integer not null PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
Row3 varchar(60),
foreign key(id_venda) references vendas(id_venda)
);

create table forma_de_pagamento(
id_venda integer not null PRIMARY KEY,
Row1 varchar(60),
Row2 varchar(60),
Row3 varchar(60),
foreign key(id_venda) references vendas(id_venda)
);
