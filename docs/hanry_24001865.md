# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Hanry de Sousa
RA: 24001865
Data: 25/03/2026

---

# 1. Definição do MVP
Descreva aqui qual parte do sistema foi incluída no seu MVP.
Explique claramente:

Meu MVP cobre o processo principal de operação da farmácia: a venda de balcão (desde a identificação do produto e cliente até a emissão do comprovante) e a gestão essencial de estoque e compras.

O que está dentro do MVP: Cadastro e consulta de produtos/clientes, realização de vendas com baixa automática de estoque, validação de receitas, e registro de compras de fornecedores com integração financeira básica (contas a pagar e receber).

O que está fora do MVP: Relatórios estratégicos complexos (BI), logística de transferência de produtos entre filiais e gestão de folha de pagamento de funcionários.

Por que você fez essas escolhas: O foco é resolver os problemas mais urgentes da rede (estoques divergentes e falhas em lançamentos diários), garantindo que a farmácia opere com integridade de dados e rapidez no atendimento desde o primeiro dia.

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva cada RN de forma clara.

**RN01 —** Medicamentos controlados só podem ser vendidos mediante autorização do perfil Farmacêutico.
**RN02 —** O sistema deve bloquear a finalização de uma venda caso a quantidade solicitada seja maior que o saldo em estoque.
**RN03 —** Vendas a prazo (convênio) são permitidas apenas para clientes previamente cadastrados.
**RN04 —** Todo registro de compra de um fornecedor deve gerar automaticamente um lançamento em Contas a Pagar.
**RN05 —** Toda venda a prazo deve gerar automaticamente um lançamento em Contas a Receber.

---

# 3. Requisitos Funcionais (mínimo: 8)

Liste os requisitos funcionais do seu MVP.

**RF01 —** O sistema deve permitir o cadastro e consulta de produtos por nome e código de barras.
**RF02 —** O sistema deve atualizar o estoque automaticamente após cada venda ou compra.
**RF03 —** O sistema deve permitir o registro de vendas com pagamento à vista e a prazo.
**RF04 —** O sistema deve permitir o cadastro rápido de clientes.
**RF05 —** O sistema deve emitir um comprovante ao final de cada venda.
**RF06 —** O sistema deve registrar compras de fornecedores contendo data, valor e produtos.
**RF07 —** O sistema deve gerar alertas quando um produto atingir o nível mínimo de estoque.
**RF08 —** O sistema deve permitir a alteração de status (Aberta, Paga) de Contas a Pagar/Receber.

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 —** O sistema deve possuir controle de acesso baseado em perfis (Atendente, Farmacêutico, Gerente).
**RNF02 —** O sistema deve ser acessível via navegador Web.
**RNF03 —** O tempo de resposta na consulta de estoque não deve ultrapassar 2 segundos.
**RNF04 —** O sistema deve ser operável via atalhos de teclado para agilizar o balcão.

---

# 5.  Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
os 10 casos
relação entre eles e atores
pelo menos 3 includes
pelo menos 3 extends

<img width="287" height="644" alt="diagrama_casos_de_uso" src="https://github.com/user-attachments/assets/1a63bc67-4751-4c22-981d-ba9be5e7a2b2" />


---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UCXX — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

UC01 — Realizar Venda
Ator(es): Atendente
Descrição: Registro de venda de itens no balcão.
Pré-condições: Usuário logado e produtos cadastrados.
Pós-condições: Venda concluída e estoque atualizado.

Fluxo Principal
1. Atendente inicia a venda.
2. Consulta o produto e verifica estoque.
3. Adiciona o produto ao carrinho.
4. Informa a forma de pagamento e finaliza.
Fluxos Alternativos / Exceções
FA01 — Cliente não cadastrado: Aciona o cadastro de cliente.
FA02 — Remédio Controlado: Exige autorização do farmacêutico.
Relacionamentos
Include: UC02 (Consultar Produto), UC03 (Verificar Estoque)
Extend: UC04 (Cadastrar Cliente), UC05 (Autorizar Venda Controlada), UC06 (Registrar Venda a Prazo)

<img width="352" height="844" alt="diagrama_uc01" src="https://github.com/user-attachments/assets/8625dfb4-2fde-4698-92c4-e0b30ce0ab97" />


UC02 — Consultar Produto
Ator(es): Atendente, Gerente
Descrição: Busca detalhes de um produto.
Pré-condições: Sistema online.
Pós-condições: Detalhes do produto exibidos.

Fluxo Principal
1. Usuário digita nome ou código.
2. Sistema busca no banco.
3. Sistema retorna preço e descrição.
Fluxos Alternativos / Exceções
FA01 — Produto não encontrado: Exibe aviso de erro.
Relacionamentos
Include: Nenhum
Extend: Nenhum

<img width="561" height="307" alt="diagrama_uc02" src="https://github.com/user-attachments/assets/6f08a48c-f946-4039-928a-1060fb4157a6" />


UC03 — Verificar Estoque
Ator(es): Sistema
Descrição: Checa a quantidade disponível de um item.
Pré-condições: Produto selecionado.
Pós-condições: Retorna a quantidade.

Fluxo Principal
1. Recebe ID do produto.
2. Consulta tabela de estoque.
3. Retorna saldo.
Fluxos Alternativos / Exceções
FA01 — Falha de Conexão: Retorna erro de timeout.
Relacionamentos
Include: Nenhum
Extend: Nenhum

<img width="499" height="307" alt="diagrama_uc03" src="https://github.com/user-attachments/assets/6cb6c842-83ec-446e-9cdb-06931bf2e8c2" />


UC04 — Cadastrar Cliente
Ator(es): Atendente
Descrição: Registra um novo cliente.
Pré-condições: Nenhuma.
Pós-condições: Cliente salvo no banco.

Fluxo Principal
1. Solicita CPF e Nome.
2. Preenche dados.
3. Salva cadastro.
Fluxos Alternativos / Exceções
FA01 — CPF já cadastrado: Carrega o cadastro existente.
Relacionamentos
Include: Nenhum
Extend: Estende UC01

<img width="533" height="307" alt="diagrama_uc04" src="https://github.com/user-attachments/assets/7f5272b7-27eb-4d67-a910-5352afa3a323" />


UC05 — Autorizar Venda Controlada
Ator(es): Farmacêutico
Descrição: Liberação de medicamento restrito.
Pré-condições: Produto restrito no carrinho.
Pós-condições: Item liberado para venda.

Fluxo Principal
1. Sistema pede senha.
2. Farmacêutico verifica receita.
3. Insere credenciais e libera.
Fluxos Alternativos / Exceções
FA01 — Senha Incorreta: Bloqueia a venda.
Relacionamentos
Include: Nenhum
Extend: Estende UC01

<img width="588" height="361" alt="diagrama_uc05" src="https://github.com/user-attachments/assets/146d530f-1f41-4d18-b0fd-348cfe6a0646" />


UC06 — Registrar Venda a Prazo
Ator(es): Atendente
Descrição: Processa pagamento via convênio.
Pré-condições: Cliente cadastrado.
Pós-condições: Conta a receber gerada.

Fluxo Principal
1. Escolhe "A Prazo".
2. Verifica limite do cliente.
3. Gera duplicata.
Fluxos Alternativos / Exceções
FA01 — Cliente com pendência: Bloqueia venda.
Relacionamentos
Include: Nenhum
Extend: Estende UC01

<img width="693" height="307" alt="diagrama_uc06" src="https://github.com/user-attachments/assets/ef942383-5434-45e0-a2ce-9e5bd5abf665" />


UC07 — Registrar Compra de Fornecedor
Ator(es): Gerente
Descrição: Entrada de nota fiscal.
Pré-condições: Fornecedor cadastrado.
Pós-condições: Estoque atualizado.

Fluxo Principal
1. Importa XML da nota.
2. Confirma produtos.
3. Salva entrada.
Fluxos Alternativos / Exceções
FA01 — Produto Novo: Exige cadastro do item.
Relacionamentos
Include: UC08 (Atualizar Estoque)
Extend: Nenhum

<img width="289" height="498" alt="diagrama_uc07" src="https://github.com/user-attachments/assets/2c157d32-e5dd-4213-bef8-50fa14de59ae" />


UC08 — Atualizar Estoque
Ator(es): Sistema
Descrição: Soma ou subtrai saldo.
Pré-condições: Venda ou compra confirmada.
Pós-condições: Saldo alterado.

Fluxo Principal
1. Recebe gatilho e quantidade.
2. Atualiza banco de dados.
3. Grava log.
Fluxos Alternativos / Exceções
FA01 — Saldo Negativo: Aciona erro.
Relacionamentos
Include: Nenhum
Extend: Nenhum

<img width="510" height="307" alt="diagrama_uc08" src="https://github.com/user-attachments/assets/8ca9a67e-f7fa-4056-b56e-2ae78d59cccb" />


UC09 — Gerenciar Financeiro
Ator(es): Financeiro
Descrição: Baixa de contas a pagar/receber.
Pré-condições: Contas registradas.
Pós-condições: Status alterado.

Fluxo Principal
1. Acessa painel.
2. Seleciona conta aberta.
3. Registra pagamento.
Fluxos Alternativos / Exceções
FA01 — Estorno: Cancela baixa errada.
Relacionamentos
Include: Nenhum
Extend: Nenhum

<img width="612" height="361" alt="diagrama_uc09" src="https://github.com/user-attachments/assets/9543e82c-dde0-4b85-97df-adc2ca346f16" />


UC10 — Gerar Relatórios
Ator(es): Gerente
Descrição: Extração de dados de desempenho.
Pré-condições: Dados no sistema.
Pós-condições: Relatório exibido.

Fluxo Principal
1. Escolhe tipo de relatório.
2. Define período.
3. Sistema exibe dados.
Fluxos Alternativos / Exceções
FA01 — Sem dados: Exibe aviso vazio.
Relacionamentos
Include: Nenhum
Extend: Nenhum


<img width="574" height="307" alt="diagrama_uc10" src="https://github.com/user-attachments/assets/8c3e2bfe-641d-4362-96a4-22d5e5a0706a" />
