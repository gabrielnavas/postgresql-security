### Arquivo pg_hba.conf

###### É o arquivo que configura:

- O tipo de conexão.
- Quais bases de dados podem haver essa conexão.
- Quais são os usuários autorizados a fazer a conexão.
- Quais endereços de IP podem fazer essa conexão.
- Se terá algum método de criptografia de acesso do usuário.

#### Crie um usuário para a área de negócio do banco
```sql
CREATE USER my_username_here WITH PASSWORD '12345678';
```

#### Regras exemplo

- Criar a regra para qual usuário pode acessar as base de dados
- Deixe somente usuário:
	- `postgres` para acessar a base de dados `postgres` 
	- `my_username_here` para a base `application_db_name` usada para o negócio da aplicação.

```config
TYPE DATABASE USER ADDRESS METHOD

host postgres,application_db_name postgres 192.168.0.0/24 password
host application_db_name my_username_here ip_backend_app password
```

#### Use para reiniciar o banco em produção
```sql
SELECT pg_reload_conf()
```

#### Referência para esse tutorial
[link para o vídeo](https://www.youtube.com/watch?v=nt1e3BqNA0E)
