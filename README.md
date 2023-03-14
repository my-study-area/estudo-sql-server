# estudo-sql-server

```bash
# inicia o container com sql server
docker-compose up -d

# acessa sqlcmd
docker-compose exec sqlserver /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P 1234@abcd
```

```sql
-- cria banco de dados
CREATE database ESTUDOSQLSERVER;

-- lista os banco de dados
SELECT name, database_id, create_date  
FROM sys.databases;

-- lista as tabelas
SELECT * FROM sys.tables;

-- lista os campos das tabelas
SELECT * FROM information_schema.COLUMNS WHERE TABLE_NAME='TABELA DE CLIENTES';

-- descreve as colunas da tabela
exec sp_help 'TABELA DE CLIENTES'
exec sp_columns 'TABELA DE CLIENTES'
```

## Links
- [Ferramentas para analise de planos de execução](https://stackoverflow.com/questions/46040555/how-to-view-execution-plans-in-sql-server-on-linux)
- [Azure Data Studio](https://learn.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver16&)tabs=redhat-install%2Credhat-uninstall 
- [SQL Server Linux](https://learn.microsoft.com/pt-br/sql/linux/sql-server-linux-overview?view=sql-server-ver16)
- [Exemplo de DDL](https://github.com/IC12/SQL-Server/blob/main/SQL%20Server/Incluindo%20dados%20tabela%20produtos%20e%20clientes.sql)
