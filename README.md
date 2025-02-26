# Consumindo-banco-de-dados

## Requisitos
- .NET Core SDK
- Visual Studio

## Passos para Rodar

### 1. Baixar o Projeto
1. Faça o download do projeto do GitHub:
    - Acesse o repositório do projeto.
    - Clique em "Code" e depois em "Download ZIP".
    - Extraia o conteúdo do arquivo ZIP.

### 2. Abrir no Visual Studio
1. Abra o Visual Studio.
2. Clique em "Open a project or solution" e selecione o arquivo `.sln` na pasta extraída.

### 3. Restaurar Dependências
1. No Visual Studio, vá em "Tools" > "NuGet Package Manager" > "Manage NuGet Packages for Solution...".
2. Certifique-se de que todas as dependências estão instaladas.

### 4. Configurar o Banco de Dados
1. Crie o banco de dados `pedidos.db` usando uma ferramenta como DB Browser for SQLite.
2. Execute os comandos SQL abaixo para criar as tabelas:
    ```sql
    CREATE TABLE Clientes (
        Id INTEGER PRIMARY KEY AUTOINCREMENT,
        Nome TEXT NOT NULL,
        Email TEXT NOT NULL
    );

    CREATE TABLE Produtos (
        Id INTEGER PRIMARY KEY AUTOINCREMENT,
        Nome TEXT NOT NULL,
        Preco REAL NOT NULL,
        Estoque INTEGER NOT NULL
    );

    CREATE TABLE Pedidos (
        Id INTEGER PRIMARY KEY AUTOINCREMENT,
        ClienteId INTEGER NOT NULL,
        DataPedido TEXT NOT NULL,
        FOREIGN KEY (ClienteId) REFERENCES Clientes(Id)
    );

    CREATE TABLE ItensPedido (
        Id INTEGER PRIMARY KEY AUTOINCREMENT,
        PedidoId INTEGER NOT NULL,
        ProdutoId INTEGER NOT NULL,
        Quantidade INTEGER NOT NULL,
        PrecoTotal REAL NOT NULL,
        FOREIGN KEY (PedidoId) REFERENCES Pedidos(Id),
        FOREIGN KEY (ProdutoId) REFERENCES Produtos(Id)
    );
    ```

### 5. Executar o Programa
1. No Visual Studio, clique em "Start" ou pressione `F5` para compilar e executar o projeto.
2. Use o menu para interagir com o sistema.
