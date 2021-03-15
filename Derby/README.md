# Apache Derby
Apache Derby é um sistema de gerenciamento de banco de dados relacional Java que pode ser embutido em programas Java e usado para processamento de transações online. Consome apenas 2 MB de espaço em disco. O Apache Derby é desenvolvido como um projeto open source sob a Apache 2.0 licence.

## SET DERBY_DATA
```
DERBY_DATA=/opt/apache/db-derby/data
```

## SET DERBY_INSTALL
```
DERBY_INSTALL=/opt/apache/db-derby/10.14.2.0
```

## VERIFY DERBY
```
java org.apache.derby.tools.sysinfo
```

## SETUP SERVER MODE
```
$DERBY_INSTALL\lib\derbytools.jar:$DERBY_INSTALL\lib\derbynet.jar:$DERBY_INSTALL\lib\derbyclient.jar;.
```

## START SERVER
```
java -jar $DERBY_INSTALL\lib\derbyrun.jar server start
```

## SHUTDOWN SERVER
```
java -jar $DERBY_INSTALL\lib\derbyrun.jar server shutdown
```

## CREATE DATABASE
```sh
java org.apache.derby.tools.ij
ij> connect 'jdbc:derby://localhost:1527/dbtest;create=true';
ij> connect 'jdbc:derby://localhost:1527/dbtest';
```

```sql
CREATE TABLE t_user(
    user_id BIGINT  NOT NULL,
    user_name VARCHAR(80)  NOT NULL,
    user_email VARCHAR(80)  NOT NULL,
    user_login VARCHAR(16)  NOT NULL,
    user_password VARCHAR(32)  NOT NULL,
    user_created_on TIMESTAMP  NOT NULL,    
    user_status CHAR(1) NOT NULL,
    CONSTRAINT PK_user_id PRIMARY KEY(user_id),
    CONSTRAINT UQ_user_login UNIQUE(user_login),
    CONSTRAINT CK_user_status CHECK(user_status IN ('A', 'I'))
);

INSERT INTO t_user VALUES(1, 'User Name', 'username@test.com', 'username', '5f4dcc3b5aa765d61d8327deb882cf99', CURRENT_TIMESTAMP, 'A');
COMMIT;
```

```
java org.apache.derby.tools.ij
connect 'jdbc:derby://localhost:1527/$DERBY_DATA/profin;create=true';
```