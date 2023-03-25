# estudo-sql-server

```bash
# inicia o container com sql server
docker-compose up -d

# acessa sqlcmd
docker-compose exec sqlserver /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P 1234@abcd
```

Para restaurar um banco de dados no Azure Data Studio realize os seguintes passos:

```bash
docker cp db-data/AdventureWorksDW2019.bak  estudo-sql-server-sqlserver-1:/mnt/
# download dos backups: https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks
```
- [Habilite feature preview](https://learn.microsoft.com/pt-br/sql/azure-data-studio/preview-features?view=sql-server-ver16)
- [Restaure o banco de dados](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=data-studio#restore-to-sql-server)
- [Vídeo com demostração dos passos](https://www.youtube.com/watch?v=L1c4ZDRw0vg&ab_channel=NiravGandhi)

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


-- mostra a quantidade de linhas por tabela
SELECT t.name TableName, i.rows Records
FROM sysobjects t, sysindexes i
WHERE t.xtype = 'U' and i.id = t.id and i.indid in (0,1)
ORDER BY Records DESC
```

## Links
- [Ferramentas para analise de planos de execução](https://stackoverflow.com/questions/46040555/how-to-view-execution-plans-in-sql-server-on-linux)
- [Azure Data Studio](https://learn.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver16&)tabs=redhat-install%2Credhat-uninstall 
- [SQL Server Linux](https://learn.microsoft.com/pt-br/sql/linux/sql-server-linux-overview?view=sql-server-ver16)
- [Exemplo de DDL](https://github.com/IC12/SQL-Server/blob/main/SQL%20Server/Incluindo%20dados%20tabela%20produtos%20e%20clientes.sql)
