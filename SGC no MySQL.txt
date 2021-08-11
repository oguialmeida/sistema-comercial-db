create database sgc;  
use sgc;             

create table armazem(                
id int not null auto_increment,      
nome varchar(30) not null,
primary key (id)
);
create table peca(
id int not null auto_increment,
nome varchar(30) not null, 
constraint armazem_id foreign key (id) references armazem(id),
primary key (id)
);
create table cliente(
id int not null auto_increment,
nome varchar(30) not null, 
credito decimal(5,2),
primary key (id)
); 
create table vendedor(
id int not null auto_increment,
nome varchar(30) not null, 
primary key (id)
);
create table pedido(
id int not null auto_increment,
comissao decimal(5,2) not null,
constraint cliente_id foreign key (id) references cliente(id),
constraint vendedor_id foreign key (id) references vendedor(id),
primary key (id)
);
create table item(
id int not null auto_increment,
quantidade int not null, 
preco decimal(5,2) not null,
constraint peca_id foreign key (id) references peca(id),
constraint pedido_id foreign key (id) references pedido(id),
primary key (id)
);