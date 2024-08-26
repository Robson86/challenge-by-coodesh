# Challenge-by-coodesh


## Consulta de vendas
## Linguagem SQL
## Instalar SQL Server

Para instalar o SQL Server, você pode seguir os passos abaixo. Vou te guiar pelo processo de instalação do SQL Server e do SQL Server Management Studio (SSMS):
Baixar o SQL Server:
Acesse a página de downloads da Microsoft e escolha a edição que melhor se adapta às suas necessidades. Para uso pessoal e testes, a edição Developer é uma boa opção, pois é gratuita.
Executar o Instalador:
Após o download, execute o arquivo de instalação. Escolha a opção de instalação personalizada para selecionar os componentes que deseja instalar.
Configurar a Instalação:
Aceite os termos de licença e siga as instruções do assistente de instalação. Você pode optar por instalar apenas os serviços essenciais, como o Database Engine Services.
Defina o modo de autenticação (Windows Authentication ou Mixed Mode) e configure a senha para o usuário sa se escolher o modo misto.
Instalar o SQL Server Management Studio (SSMS):
Baixe o SSMS da página oficial da Microsoft.
Execute o instalador do SSMS e siga as instruções para concluir a instalação.
Conectar ao SQL Server:
Abra o SSMS e conecte-se ao seu servidor SQL usando a autenticação configurada durante a instalação.

## Códigos do Projeto

### Listar todos Clientes que não tenham realizado uma compra;
SELECT c.*
FROM customers c
LEFT JOIN orders o ON c.custorme_id = o.customer_id
WHERE o.customer_id IS NULL

### Listar os Produtos que não tenham sido comprados
SELECT p.*
FROM products p
LEFT JOIN order_items oi ON p.product_id = oi.product_id
WHERE c.item_id IS NULL

### Listar os Produtos sem Estoque;
SELECT *
FROM products p
JOIN stocks s ON p.product_id = s.product_id
WHERE quantity = 0

### Agrupar a quantidade de vendas que uma determinada Marca por Loja.
SELECT s.stores, s.store_name, p.product_id, p.product_name, SUM(oi.quantity) AS TotalVendas
FROM orders o
JOIN order_items oi ON o.order_id = p.order_id
JOIN products p ON p.product_id = oi.product_id
JOIN stores s ON s.store_id = o.store_id
GROUP BY s.stores, s.store_name, p.product_id, p.product_name

### Listar os Funcionarios que não estejam relacionados a um Pedido.
SELECT s.*
FROM staffs s
LEFT JOIN orders o ON s.staff_id = o.staff_id
WHERE s.staffs IS NULL;



