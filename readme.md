# Comandos de banco de dados

### OBs:  Executar o comandos
```
Ctrl + Enter
```

### Criar Database
* Local para criar as tabelas do sistema 
```
create database Nome_Database;
```

### Selecionar Database
```
use Nome_Database;
```
<hr>

## Projeto site Ecommerce 
* Tabela de usuarios
* Tabela de produtos
* Tabela de carrinho de compras

### Criar tabela de usuarios
```
create table usuarios{
    id int not null auto_autoincrement, 
    nome varchar(120) not null,
    email varchar(120) not null,
    senha varchar(120) not null,
    primary key(id)
};
```

* Id: Identificador de cada registro
* Not null: Campo obrigatorio, não pode ser nulo
* Auto_Autoincrement: Soma +1 no último registro de id
* Varchar(120): Campo de texto com 120 caracteres


### Criar tabela de produtos

```
create table produtos{
    id int not null auto_autoincrement, 
   modelo varchar(120),
   nome varchar(120) not null,
   valor float  not null,
   primary key(id)
};
```

### Criar tabela de carrinho

```
create table carrinho{
    id int not null auto_autoincrement, 
    id_usuario int not null,
    id_produto int not null,
    primary key(id)
    foreign key(id_usuario) references usuarios(id),
    foreign key(id_produto) references produto(id)
};
```
* Foreign Key: Chave estrangeira que recebe a referencia de outra tabela.
* References: Atributo para definir a tabela e o campo estrangeiro.

### Inserir usuarios
```
insert into usuarios(nome, email, senha) values('Renato', 'renato@gmail.com','secret');
```
### Inserir produtos
```
insert into produtos(modelo, nome e valor) values('nike', 'camiseta', 129.90);
```
### Inserir carrinho
```
insert into carrinho(id_usuario, id_produto) values(43, 234);
insert into carrinho(id_usuario, id_produto) values(3, 23);
```

### Listar todas as informações/colunas dos usuarios: TODOS OS CAMPOS
```
select * from usuarios;
```

### Listar apenas os nomes dos usuarios: Campo sozinho
```
select nome from usuarios;
```
### Listar nome e email: 2 campos ou +
```
select nome. email from usarios;
```

### Listar usuarios pelo id = buscar por uma caracteristica especifica
```
select * from usuario where id = 23;
```

### Verificar produtos no carrinho pelo id do usuario: acessar informação de 2 tabelas em uma só
```
select p.nome from produtos p, carrinho c
where c.id_usuario = 23 and p.id = c.id_produtos;

```