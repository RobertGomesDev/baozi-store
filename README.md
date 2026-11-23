# API REST - Baozi Store

Trabalho da disciplina Desenvolvimento Web Back-End. É uma API REST para controlar os clientes, os produtos e os pedidos da Baozi Store.

## Tecnologias
- Java 17
- Spring Boot 3.5 (Spring Web e Spring Data JPA)
- Banco relacional H2 em modo arquivo; o MySQL também pode ser usado, veja abaixo
- Postman para os testes

## Estrutura (MVC)
```
src/main/java/com/baozistore
├── BaoziStoreApplication.java
├── model/        Cliente, Produto, Pedido
├── repository/   ClienteRepository, ProdutoRepository, PedidoRepository
└── controller/   ClienteController, ProdutoController, PedidoController
```

## Como executar
1. Instale o JDK 17 ou mais recente.
2. Abra a pasta no IntelliJ IDEA ou no VS Code (com o Extension Pack for Java) e rode a classe `BaoziStoreApplication`.
   Se preferir o terminal, com o Maven instalado: `mvn spring-boot:run`
3. A API sobe em `http://localhost:8080`.
4. O console do H2 fica em `http://localhost:8080/h2-console`. Use JDBC URL `jdbc:h2:file:./data/baozistore`, usuário `sa` e senha vazia.

### Usar MySQL em vez de H2
No arquivo `src/main/resources/application.properties`, comente o bloco do H2, descomente o bloco do MySQL e coloque a sua senha.

## Endpoints
| Método | Endpoint | Descrição |
|---|---|---|
| POST | `/clientes` | Cria um cliente |
| GET | `/clientes` | Lista todos os clientes |
| GET | `/clientes/{id}` | Consulta um cliente pelo ID |
| PUT | `/clientes/{id}` | Atualiza um cliente (opcional) |
| DELETE | `/clientes/{id}` | Apaga um cliente |
| POST | `/produtos` | Cria um produto |
| GET | `/produtos` | Lista todos os produtos |
| GET | `/produtos/{id}` | Consulta um produto pelo ID |
| PUT | `/produtos/{id}` | Atualiza um produto (opcional) |
| DELETE | `/produtos/{id}` | Apaga um produto |
| POST | `/pedidos` | Registra um pedido |
| GET | `/pedidos` | Lista todos os pedidos |
| GET | `/pedidos/{id}` | Consulta um pedido pelo ID |
| PUT | `/pedidos/{id}` | Atualiza um pedido (opcional) |
| DELETE | `/pedidos/{id}` | Apaga um pedido |

### Exemplos de JSON
```json
POST /clientes  {"nome": "SeuNome1234567", "clienteDesde": "2026-11-23"}
POST /produtos  {"nome": "Baozi Tradicional de Porco", "preco": 7.50, "estoque": true}
POST /pedidos   {"clienteId": 1, "produtoId": 1, "quantidade": 6}
```

A coleção pronta para o Postman está em `BaoziStore.postman_collection.json`.
