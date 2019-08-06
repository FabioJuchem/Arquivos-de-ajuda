





Liquibase

#### Opcional

No banco de dados Oracle

SELECT ID, AUTHOR, FILENAME, DATEEXECUTED, ORDEREXECUTED, EXECTYPE, MD5SUM, DESCRIPTION, COMMENTS, TAG, LIQUIBASE, CONTEXTS, LABELS, DEPLOYMENT_ID
FROM COMPLIANCE_DENUNCIA.DATABASECHANGELOG;

para setar configurações para o oracle script no banco de dados

 



#### no arquivo application.yaml

  liquibase:
    change-log: classpath:liquibase/changelog.yaml
	

​	



#### acrescentar dependencia no arquivo pom.xml

	<!-- Liquibase -->
		<dependency>
			<groupId>org.liquibase</groupId>
			<artifactId>liquibase-core</artifactId>
		</dependency>





####  criar arquivo changelog.yaml dentro de resource/liquibase e adicionar o seguinte codigo

databaseChangeLog:
    - includeAll:
        path: liquibase/scripts/
		

#### Criar  pasta scripts**

#### criar os arquivos com scripts SQL: exemplo = V000001_CREATE_PERSON.sql

exemplo de script
create table  person (
    id number not null constraint PK_PERSON primary key ,
    name varchar2(100) not null,
    cpf varchar2(50) not null,
    email varchar2(50) not null,
    phone varchar2(50) not null,
    complaince_id number constraint FK_PERSON_COMPLAINCE references complaince(id)
)