# OS-Oficina-Mecanica
Sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica

# Esquema do Banco de Dados

## Tabelas

### Clientes

*   **idClientes** (INT, Chave Primária)
*   **nome** (VARCHAR(45))
*   **endereco** (VARCHAR(4... - Incompleto)
*   **telefone** (VARCHAR(45))

### Veiculos

*   **veiculo\_id** (INT, Chave Primária)
*   **marca** (VARCHAR(45))
*   **modelo** (VARCHAR(45))
*   **ano** (INT)
*   **placa** (VARCHAR(45))
*   **Clientes\_idClientes** (Chave Estrangeira para Clientes)

### Pecas

*   **peca\_id** (INT, Chave Primária)
*   **descricao** (VARCHAR(4... - Incompleto)
*   **valor** (FLOAT)

### OrdensServico

*   **os\_id** (INT, Chave Primária)
*   **data\_emissao** (DATE)
*   **data\_entrega** (DATE)
*   **valor\_total** (FLOAT)
*   **status** (VARCHAR(45))
*   **data\_conclusao** (DATE)
*   **Veiculos\_veiculo\_id** (Chave Estrangeira para Veiculos)
*   **Veiculos\_Clientes\_idClientes** (Chave Estrangeira para Veiculos)

### Mecanicos

*   **mecanico\_id** (INT, Chave Primária)
*   **nome** (VARCHAR(45))
*   **endereco** (VARCHAR(45))
*   **especialidade** (VARCHAR(4... - Incompleto)
*   **Mecanicoscol** (VARCHAR(45))

### Servicos

*   **servico\_id** (INT, Chave Primária)
*   **descricao** (VARCHAR(4... - Incompleto)
*   **valor\_mao\_obra** (FLOAT)

### PecasServicosOS

*   **Pecas\_peca\_id** (INT, Chave Estrangeira para Pecas)
*   **OS/Servico\_OrdensServico\_os\_id** (INT, Chave Estrangeira para OrdensServico)
*   **OS/Servico\_Servicos\_servico\_id** (INT, Chave Estrangeira para Servicos)

### EquipeMecanicos

*   **Mecanicos\_mecanico\_id** (INT, Chave Estrangeira para Mecanicos)
*   **OrdensServico\_os\_id** (INT, Chave Estrangeira para OrdensServico)

### ServicosOS

*   **OrdensServico\_os\_id** (INT, Chave Estrangeira para OrdensServico)
*   **Servicos\_servico\_id** (INT, Chave Estrangeira para Servicos)

## Relacionamentos

*   **Clientes** 1:N **Veiculos**
*   **Veiculos** 1:N **OrdensServico**
*   **Pecas** N:N:N **OrdensServico** e **Servicos** (através de **PecasServicosOS**)
*   **OrdensServico** N:N **Mecanicos** (através de **EquipeMecanicos**)
*   **OrdensServico** N:N **Servicos** (através de **ServicosOS**)
