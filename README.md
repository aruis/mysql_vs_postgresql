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

### 数据示例

| id | v\_method | v\_uri | v\_ip | i\_status | v\_type | v\_browser | b\_success | v\_application | v\_data\_id | v\_alias\_at\_app\_module | v\_alias\_at\_app\_module\_function | b\_skip | id\_at\_auth\_user | t\_create | v\_body | id\_at\_app\_module | v\_device |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| bba5ef6a\_76cf\_4811\_a5dd\_182ceaf51a15 | GET | /api/platform/dictcategory/view/CARRIER\_UNIT/children/app\_dict | 0:0:0:0:0:0:0:1 | 200 | 06 | Chrome 8 | true | platform | CARRIER\_UNIT | dictcategory | view | true | b66f83d8\_e87c\_4fe9\_bec6\_357bd2e998bd | 2020-12-02 16:10:56.629945 | NULL | 179b0a11\_94c9\_41bb\_a788\_79a99f6096e7 | PC |
| 648a04ca\_8e13\_4c63\_9fea\_8fa69308217c | GET | /api/szda/lendMnt/lendView | 0:0:0:0:0:0:0:1 | 200 | 06 | Chrome 8 | true | szda | NULL | lendMnt | lendView | true | b66f83d8\_e87c\_4fe9\_bec6\_357bd2e998bd | 2020-12-02 16:11:00.161490 | NULL | 53a8e8ee\_98ee\_4e32\_8425\_4042891d5b20 | PC |
| d7fb3d8a\_da8d\_4699\_8c54\_e2a37329a128 | GET | /api/szda/digitalArchive/detailView | 0:0:0:0:0:0:0:1 | 200 | 06 | Chrome 8 | true | szda | NULL | digitalArchive | detailView | true | b66f83d8\_e87c\_4fe9\_bec6\_357bd2e998bd | 2020-12-02 16:12:28.795853 | NULL | 457338e5\_abe8\_44fd\_aa78\_01f789e47289 | PC |
| 285077fc\_0c4d\_43bf\_bf91\_51dd4fb60bb9 | GET | /api/msg/app/inBox/b66f83d8\_e87c\_4fe9\_bec6\_357bd2e998bd | 0:0:0:0:0:0:0:1 | 200 | 06 | Chrome 8 | true | msg | b66f83d8\_e87c\_4fe9\_bec6\_357bd2e998bd | app | inBox | true | b66f83d8\_e87c\_4fe9\_bec6\_357bd2e998bd | 2020-12-02 16:13:26.954893 | NULL | NULL | PC |
| 483e8486\_c340\_40f6\_bc87\_5ea7afa302aa | GET | /api/platform/dictcategory/view/SECRET\_LEVEL/children/app\_dict | 0:0:0:0:0:0:0:1 | 200 | 06 | Chrome 8 | true | platform | SECRET\_LEVEL | dictcategory | view | true | b66f83d8\_e87c\_4fe9\_bec6\_357bd2e998bd | 2020-12-02 16:13:27.138294 | NULL | 179b0a11\_94c9\_41bb\_a788\_79a99f6096e7 | PC |


