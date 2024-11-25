# Desafio DIO - Construindo um Esquema Conceitual para Banco De dados

## Sistema de Gerenciamento de Oficina Mecânica

Este projeto consiste na criação de um banco de dados relacional para gerenciar as operações de uma oficina mecânica, utilizando o MySQL. Ele foi desenvolvido com base em um modelo conceitual que define as principais entidades e seus relacionamentos.

### Objetivo

Fornecer uma estrutura eficiente para gerenciar:
- Cadastro de clientes e veículos.
- Registro de ordens de serviço.
- Controle de serviços executados e peças utilizadas.
- Gerenciamento de equipes de mecânicos.

### Estrutura do Banco de Dados

O banco de dados foi projetado com as seguintes tabelas:

#### 1. **Cliente**
Armazena informações dos clientes.
- `id_cliente`: Identificador único.
- `nome`: Nome do cliente.
- `endereco`: Endereço do cliente.
- `telefone`: Telefone para contato.

#### 2. **Veiculo**
Registra os veículos associados aos clientes.
- `id_veiculo`: Identificador único.
- `placa`: Placa do veículo (única).
- `modelo`: Modelo do veículo.
- `marca`: Marca do veículo.
- `ano`: Ano de fabricação.
- `id_cliente`: Referência ao cliente proprietário.

#### 3. **Mecanico**
Armazena os dados dos mecânicos.
- `id_mecanico`: Identificador único.
- `nome`: Nome do mecânico.
- `endereco`: Endereço do mecânico.
- `especialidade`: Área de atuação.

#### 4. **OrdemServico**
Registra as ordens de serviço.
- `id_os`: Identificador único.
- `data_emissao`: Data de emissão da OS.
- `data_conclusao`: Data de conclusão dos trabalhos.
- `valor_total`: Valor total da OS.
- `status`: Status atual da OS.
- `id_veiculo`: Referência ao veículo associado.

#### 5. **Servico**
Contém informações sobre os serviços disponíveis.
- `id_servico`: Identificador único.
- `descricao`: Descrição do serviço.
- `valor_mao_obra`: Valor da mão de obra para o serviço.

#### 6. **Peca**
Lista as peças disponíveis e seus preços.
- `id_peca`: Identificador único.
- `descricao`: Descrição da peça.
- `valor`: Preço da peça.

#### 7. **ItemServico**
Associa serviços às ordens de serviço.
- `id_item_servico`: Identificador único.
- `id_os`: Referência à ordem de serviço.
- `id_servico`: Referência ao serviço.
- `quantidade`: Quantidade do serviço.
- `valor`: Valor total do serviço.

#### 8. **ItemPeca**
Relaciona peças às ordens de serviço.
- `id_item_peca`: Identificador único.
- `id_os`: Referência à ordem de serviço.
- `id_peca`: Referência à peça.
- `quantidade`: Quantidade utilizada.
- `valor`: Valor total das peças.

#### 9. **Equipe**
Gerencia a associação de mecânicos às ordens de serviço.
- `id_equipe`: Identificador único.
- `id_os`: Referência à ordem de serviço.
- `id_mecanico`: Referência ao mecânico.

### Diagrama Conceitual

(O diagrama conceitual pode ser incluído aqui como uma imagem ou link caso tenha sido gerado.)

### Como Executar o Script

1. Certifique-se de ter o MySQL instalado em sua máquina.
2. Crie um banco de dados no MySQL:
   ```sql
   CREATE DATABASE Oficina;
   ```
3. Acesse o banco de dados criado:
   ```sql
   USE Oficina;
   ```
4. Execute o script SQL contido no arquivo `oficina.sql` para criar as tabelas e relacionamentos.

### Futuras Implementações

- Adicionar triggers para atualizar automaticamente o `valor_total` na tabela `OrdemServico`.
- Implementar controle de acesso para diferentes tipos de usuários (administradores, mecânicos, etc.).
- Criar stored procedures para relatórios automáticos.
