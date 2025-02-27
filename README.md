# Projeto-Conceitual-de-Banco-de-Dados-E-COMMERCE
Desafio do BOOTCAMP DIO Refinando um Projeto Conceitual de Banco de Dados – E-COMMERCE
Este README fornece uma visão geral do modelo conceitual de um banco de dados para um sistema de gerenciamento de clientes, produtos, pedidos, e transações. O modelo foi desenvolvido para abranger as seguintes entidades: Cliente, Produto, Fornecedor, Pedido, Forma de Pagamento, Estoque, Entrega e Devolução. Cada entidade é descrita com seus atributos e os relacionamentos com outras entidades.
Entidades e Relacionamentos
Cliente
id_cliente (PK): Identificador único do cliente.

tipo_cliente: Enumeração para definir se é PF (Pessoa Física) ou PJ (Pessoa Jurídica).

nome: Nome do cliente (para PF).

razao_social: Razão social do cliente (para PJ).

cpf: CPF do cliente (para PF).

cnpj: CNPJ do cliente (para PJ).

email: Endereço de email.

telefone: Número de telefone.

endereco: Endereço do cliente.

Relacionamentos:

Cliente ↔ Pedido: 1:N (Um cliente pode fazer muitos pedidos)

Produto
id_produto (PK): Identificador único do produto.

nome: Nome do produto.

descricao: Descrição detalhada do produto.

preco: Preço do produto.

id_fornecedor (FK): Identificador do fornecedor.

categoria: Categoria do produto.

peso: Peso do produto.

dimensoes: Dimensões do produto.

Relacionamentos:

Produto ↔ Estoque: 1:N (Um produto pode estar em muitos registros de estoque)

Produto ↔ ItemPedido: 1:N (Um produto pode estar em muitos itens de pedido)

Fornecedor
id_fornecedor (PK): Identificador único do fornecedor.

nome: Nome do fornecedor.

cnpj: CNPJ do fornecedor.

telefone: Número de telefone.

endereco: Endereço do fornecedor.

Relacionamentos:

Fornecedor ↔ Produto: 1:N (Um fornecedor pode fornecer muitos produtos)

Pedido
id_pedido (PK): Identificador único do pedido.

id_cliente (FK): Identificador do cliente.

data_pedido: Data em que o pedido foi realizado.

status_pedido: Enumeração para definir o status do pedido (Pendente, Pago, Enviado, Entregue, Cancelado).

valor_total: Valor total do pedido.

id_pagamento (FK): Identificador do pagamento.
Relacionamentos:

Pedido ↔ Cliente: N:1 (Muitos pedidos são feitos por um cliente)

Pedido ↔ Forma de Pagamento: 1:1 (Um pedido tem uma forma de pagamento)

Pedido ↔ Entrega: 1:1 (Um pedido tem uma entrega)

Pedido ↔ Devolução: 1:1 (Um pedido pode ter uma devolução)

Pedido ↔ ItemPedido: 1:N (Um pedido pode conter muitos itens de pedido)

Forma de Pagamento
id_pagamento (PK): Identificador único do pagamento.

id_pedido (FK): Identificador do pedido.

metodo: Enumeração para definir o método de pagamento (Cartão de Crédito, Boleto, Pix, etc.).

status_pagamento: Enumeração para definir o status do pagamento (Aprovado, Pendente, Recusado).

valor_pago: Valor pago no método de pagamento.

Relacionamentos:

Forma de Pagamento ↔ Pedido: N:1 (Muitas formas de pagamento referenciam um pedido)

Estoque
id_estoque (PK): Identificador único do estoque.

id_produto (FK): Identificador do produto.

quantidade_disponivel: Quantidade disponível do produto no estoque.

localizacao: Localização do estoque.

Relacionamentos:

Estoque ↔ Produto: N:1 (Muitos registros de estoque referenciam um produto)

Entrega
id_entrega (PK): Identificador único da entrega.

id_pedido (FK): Identificador do pedido.

codigo_rastreio: Código de rastreamento da entrega.

transportadora: Nome da transportadora.

prazo_estimado: Prazo estimado para a entrega.

status_entrega: Enumeração para definir o status da entrega (Em Transporte, Entregue, Extraviado).

Relacionamentos:

Entrega ↔ Pedido: N:1 (Muitas entregas referenciam um pedido)

Devolução
id_devolucao (PK): Identificador único da devolução.

id_pedido (FK): Identificador do pedido.

motivo: Motivo da devolução.

data_solicitacao: Data da solicitação de devolução.

status_devolucao: Enumeração para definir o status da devolução (Solicitada, Aprovada, Recusada, Concluída).

reembolso_valor: Valor a ser reembolsado, se aplicável.

Relacionamentos:

Devolução ↔ Pedido: N:1 (Muitas devoluções referenciam um pedido)

Tabela de Junção: ItemPedido
id_item (PK): Identificador único do item do pedido.

id_pedido (FK): Identificador do pedido.

id_produto (FK): Identificador do produto.

quantidade: Quantidade do produto no pedido.

preco_unitario: Preço unitário do produto no pedido.

Relacionamentos:

Pedido ↔ ItemPedido: 1:N (Um pedido pode conter muitos itens de pedido)

Produto ↔ ItemPedido: 1:N (Um produto pode estar em muitos itens de pedido)
