PedidoID: Deveria ter primary key e ser SERIAL
As colunas com o nome "Cliente" deveriam estar na tabela Cliente e serem referenciadas em um ClienteID com chave estrangeira
As colunas com o nome "Produto" deveriam estar na tabela Produto e serem referenciadas em um ProdutoID com chave estrangeira
A colunas com o nome "Vendedor" deveriam estar na tabela Produto e serem referenciadas em um VendedorID com chave estrangeira
A categoria deveriam estar em uma tabela diferente e serem referenciadas em um CategoriaID com chave estrangeira na tabela de Produto
A coluna EndereçoCompleto deveria ser ser dividida em Rua, Numero e complemento em uma tabela separada e ser referencia com chave estrangeira

Normalização vs Desnormalização

Normalizar 
- dados íntegros
- Sem redundancias
- Atualizações fáceis

Desnormalizar
- Consultas rápidas
- Relatórios simples
- Menos JOINs
- Dados duplicados


"Otimização prematura é a raiz de todo mal"