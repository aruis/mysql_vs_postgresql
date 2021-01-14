# MySQL 8.0.22 vs PostgreSQL 13.1

MySQL 配置文件[my.cnf](https://github.com/aruis/mysql_vs_postgresql/blob/main/my.cnf)

PostgreSQL 配置文件[postgres.conf](https://github.com/aruis/mysql_vs_postgresql/blob/main/postgresql.conf)

机器：Macbook Air M1 16G+512G

#### 建表语句

1. MySQL

```sql
create table log_access
(
    id                             varchar(40) default (uuid()) not null primary key,
    v_method                       varchar(10),
    v_uri                          varchar(200),
    v_ip                           varchar(15),
    i_status                       integer,
    v_type                         varchar(2),
    v_browser                      varchar(20),
    b_success                      boolean,
    v_application                  varchar(10),
    v_data_id                      varchar(80),
    v_alias_at_app_module          varchar(30),
    v_alias_at_app_module_function varchar(45),
    b_skip                         boolean,
    id_at_auth_user                varchar(40),
    t_create                       timestamp,
    v_body                         varchar(70),
    id_at_app_module               varchar(40),
    v_device                       varchar(10)
);
```

2. PostgreSQL

```sql
create table log_access
(
    id                             varchar default gen_random_uuid() not null primary key,
    v_method                       varchar,
    v_uri                          varchar,
    v_ip                           varchar,
    i_status                       integer,
    v_type                         varchar,
    v_browser                      varchar,
    b_success                      boolean,
    v_application                  varchar,
    v_data_id                      varchar,
    v_alias_at_app_module          varchar,
    v_alias_at_app_module_function varchar,
    b_skip                         boolean,
    id_at_auth_user                varchar,
    t_create                       timestamp,
    v_body                         varchar,
    id_at_app_module               varchar,
    v_device                       varchar
);
```


