# Banco-de-dados
Claro! Vou organizar tudo em formato de **README.md**, pronto para colocar no GitHub.

````markdown
# ☕ Banco de Dados - Loja

Este projeto apresenta um banco de dados chamado **loja**, criado em MySQL, utilizando o phpMyAdmin.

O banco possui três tabelas principais:

- 👤 Cliente
- 🛍️ Produto
- 🛒 Compra

---

## 🗄️ Criação do Banco de Dados

```sql
CREATE DATABASE loja;

USE loja;
````

---

## 👤 Tabela Cliente

A tabela `cliente` armazena os dados dos clientes.

```sql
CREATE TABLE cliente (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    telefone VARCHAR(20)
);
```

### Inserindo um cliente

```sql
INSERT INTO cliente (nome, email, telefone)
VALUES ('Rayssa', 'Raissa@email.com', '12345678');
```

---

## 🛍️ Tabela Produto

A tabela `produto` armazena os produtos disponíveis.

```sql
CREATE TABLE produto (
    id_produto INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    preco DECIMAL(10,2) NOT NULL
);
```

### Inserindo produtos

```sql
INSERT INTO produto (nome, preco)
VALUES 
('Café', 5.50),
('Bolo', 8.00),
('Pão de queijo', 4.50),
('Suco', 6.00);
```

---

## 🛒 Tabela Compra

A tabela `compra` registra as compras realizadas pelos clientes.

```sql
CREATE TABLE compra (
    id_compra INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    id_produto INT NOT NULL,
    quantidade INT NOT NULL,

    FOREIGN KEY (id_cliente) REFERENCES cliente(id_cliente),
    FOREIGN KEY (id_produto) REFERENCES produto(id_produto)
);
```

---

# 🔄 Operações CRUD

CRUD representa as quatro principais operações realizadas em um banco de dados:

| Operação | Significado   | SQL      |
| -------- | ------------- | -------- |
| Create   | Criar/inserir | `INSERT` |
| Read     | Consultar     | `SELECT` |
| Update   | Atualizar     | `UPDATE` |
| Delete   | Excluir       | `DELETE` |

---

# ➕ Inserindo Clientes

```sql
INSERT INTO cliente (nome, email, telefone)
VALUES
('Ana Silva', 'ana@gmail.com', '11999999999'),
('João Souza', 'joao@gmail.com', '11988888888'),
('Maria Santos', 'maria@gmail.com', '11977777777');
```

---

# ➕ Inserindo Produtos

```sql
INSERT INTO produto (nome, preco)
VALUES
('Notebook', 2500.00),
('Mouse', 80.00),
('Teclado', 150.00);
```

---

# ➕ Inserindo Compras

```sql
INSERT INTO compra (id_cliente, id_produto, quantidade)
VALUES
(1, 1, 1),
(1, 2, 2),
(2, 3, 1),
(3, 2, 1);
```

---

# 🔎 Consultando os Dados

### Clientes

```sql
SELECT * FROM cliente;
```

### Produtos

```sql
SELECT * FROM produto;
```

### Compras

```sql
SELECT * FROM compra;
```

---

# 🔗 Consultando quem comprou cada produto

Para mostrar o nome do cliente, o produto comprado e a quantidade:

```sql
SELECT 
    cliente.nome,
    produto.nome,
    compra.quantidade
FROM compra
JOIN cliente 
    ON cliente.id_cliente = compra.id_cliente
JOIN produto 
    ON produto.id_produto = compra.id_produto;
```

### Resultado esperado

```text
Ana Silva      Notebook    1
Ana Silva      Mouse       2
João Souza     Teclado     1
Maria Santos   Mouse       1
```

---

# ✏️ Atualizando dados

## Atualizar o telefone de um cliente

```sql
UPDATE cliente
SET telefone = '11912345678'
WHERE id_cliente = 1;
```

## Alterar o preço de um produto

```sql
UPDATE produto
SET preco = 90.00
WHERE id_produto = 2;
```

---

# 🗑️ Excluindo dados

Para excluir uma compra:

```sql
DELETE FROM compra
WHERE id_compra = 4;
```

Para verificar compras de um determinado produto:

```sql
SELECT * FROM compra
WHERE id_produto = 3;
```

Antes de excluir um produto que possui compras relacionadas, é necessário excluir as compras relacionadas primeiro:

```sql
DELETE FROM compra
WHERE id_produto = 3;
```

Depois disso, o produto pode ser excluído:

```sql
DELETE FROM produto
WHERE id_produto = 3;
```

---

# 🧩 Estrutura do Banco

O banco possui três tabelas relacionadas:

```text
CLIENTE
   │
   │ 1:N
   ▼
COMPRA
   ▲
   │ N:1
   │
PRODUTO
```

### Relacionamentos

* Um **cliente** pode realizar várias compras.
* Um **produto** pode aparecer em várias compras.
* A tabela **compra** utiliza `id_cliente` e `id_produto` como chaves estrangeiras.

---

## 🛠️ Tecnologias utilizadas

* MySQL
* phpMyAdmin
* SQL

---

## 📚 Objetivo

Este projeto foi desenvolvido para praticar conceitos de **banco de dados relacionais**, incluindo criação de tabelas, inserção, consulta, atualização, exclusão e relacionamento entre tabelas.

















<img width="952" height="324" alt="Captura de tela 2026-09-30 170548" src="https://github.com/user-attachments/assets/8e6679aa-2ef9-4ed7-9bc4-1c762e0c26b3" />


<img width="726" height="439" alt="Captura de tela 2026-10-07 084113" src="https://github.com/user-attachments/assets/4398df75-2491-4074-b8ad-e8e79a3e5e97" />

<img width="731" height="409" alt="Captura de tela 2026-10-07 083240" src="https://github.com/user-attachments/assets/d9506cb2-a930-43c9-9be0-13b45bba51b1" />
<img width="721" height="442" alt="Captura de tela 2026-10-07 085022" src="https://github.com/user-attachments/assets/25ad5e92-de10-4378-b169-f325eadf034c" />
<img width="837" height="147" alt="Captura de tela 2026-10-07 095725" src="https://github.com/user-attachments/assets/21be3d99-ae8f-4bc6-9d2f-9ded61b8b9d5" />

<h1>inserindo mais clientes</h1>

<img width="723" height="441" alt="Captura de tela 2026-10-07 084732" src="https://github.com/user-attachments/assets/347fcf17-44eb-47ec-97aa-8dde3501c2a4" />
<img width="1032" height="561" alt="Captura de tela 2026-10-07 085148" src="https://github.com/user-attachments/assets/aa593a0e-95c6-420b-8828-d5088ed2904a" />

<h1>inserindo mais produto</h1>
<img width="721" height="448" alt="Captura de tela 2026-10-07 084343" src="https://github.com/user-attachments/assets/d0e4cf03-1fd6-4948-bcc5-a2c578382ad3" />
<img width="1034" height="645" alt="Captura de tela 2026-10-07 085216" src="https://github.com/user-attachments/assets/43220e39-8055-47d1-a9f4-b884ac2ca505" />




<img width="777" height="442" alt="Captura de tela 2026-10-07 084946" src="https://github.com/user-attachments/assets/2a652a0c-8352-4fbf-8afa-b95c9179d151" />

<img width="719" height="445" alt="Captura de tela 2026-10-07 085059" src="https://github.com/user-attachments/assets/1b0fa34b-0012-4720-ba9b-8900c26bee25" />


<img width="1033" height="556" alt="Captura de tela 2026-10-07 085249" src="https://github.com/user-attachments/assets/30421a3d-226e-4f4f-b762-610eca421fff" />


<img width="825" height="441" alt="Captura de tela 2026-10-07 085519" src="https://github.com/user-attachments/assets/097caae5-0390-4b9d-9309-da7e0701c7e6" />


<img width="1011" height="521" alt="Captura de tela 2026-10-07 085358" src="https://github.com/user-attachments/assets/193f7c63-9022-4b49-a0f2-45780b0fb7c0" />
<h1>alterando o telefone</h1>

<img width="821" height="443" alt="Captura de tela 2026-10-07 085738" src="https://github.com/user-attachments/assets/7617b437-4785-4e32-88b6-d7a54cd2f32c" />

<img width="607" height="157" alt="Captura de tela 2026-10-07 090016" src="https://github.com/user-attachments/assets/d03c5756-bd3d-4ee2-802c-02e307529ec4" />
<h1>alterando o preco</h1>

<img width="723" height="439" alt="Captura de tela 2026-10-07 090135" src="https://github.com/user-attachments/assets/c93f0a9c-8801-4090-b72e-eb9f1ac3c82d" />

<img width="482" height="229" alt="Captura de tela 2026-10-07 090202" src="https://github.com/user-attachments/assets/f20c31b4-6b4b-455c-952d-dbdb2c9fe4d1" />
<h1>deletando</h1>

<img width="714" height="442" alt="Captura de tela 2026-10-07 090710" src="https://github.com/user-attachments/assets/d3bb9047-034c-4f65-848d-6e1ea43dd036" />

<img width="825" height="446" alt="Captura de tela 2026-10-07 090737" src="https://github.com/user-attachments/assets/4e894eb4-86e0-4c83-add2-2440fd9a006c" />
<img width="594" height="128" alt="Captura de tela 2026-10-07 090803" src="https://github.com/user-attachments/assets/2a3ae535-dcae-4544-94db-8eee2811184f" />



