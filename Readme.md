### Para acessar o [projeto](https://curso-node1.herokuapp.com/)

## MongoDB

 ### Para montar o ambiente:
* Após instalar o mongodb é preciso é preciso colocar a pasta 'bin' do mongo (C:\Program Files\MongoDB\Server\3.4\bin) na variável de ambiente do windows 'Path'
* Para startar o mongobd: **mongod**
* Para criar um "database": **use + nome_database**
	```
	ex. use teste
	Somente vai criar o database teste após inserir um registro dentro dele.	//Para selecionar as databases:	show dbs
	```
* Para criar uma collection (collections são semelhantes as tabelas do SQL)
	```
	db.usuarios.insert({nome:'Leonardo', idade: 22}) //vai criar a collection usuarios e inserir um registro
	```
* Exibir as collections: show collections 
* Após isso possível inserir outros registros na collection usuarios, mesmo que com outros campos.
	```
	ex. db.usuarios.insert({nome:'Leonardo', idade: 22, profissao: 'Programador'})
	```
* Fazer Select:
	```
	ex. db.usuarios.find() //no SQL: select * from usuarios
	- É possível fazer um select para ver de forma mais estruturada:
	ex. db.usuarios.find().toArray()
	```
* Para fazer update:
	```
	db.usuarios.update({profissao:'Empresario'}, {$set:{profissao:'Motorista'}})
	- Para fazer de um registro específico:
	db.usuarios.update({nome: "Vitor"}, {$set: {"idade": 99}}) //onde está passando a idade do vitor para 99
	```
* Para remover registros: 
	```
	var documento = db.usuarios.findOne({nome: 'Vitor'}); //seleciona o vitor
	db.usuarios.remove(documento); //deleta o vitor
	```
* Como apagar collecions:
	```
	db.usuarios.drop() //onde usuarios é o nome da collection
	```
* Como apagar databases:
	```
	db.dropDatabase() //necessário está usando a database
	```



* Ferramentas para usar MongoDB sem ser pelo terminal:
	* MongoVue 
	* Robomongo 
	* MongoLab

## MySQL

O MySQL está para se tornar pago, logo os criadores do MySQL criaram outro banco de dados free, o [MariaDB](https://mariadb.org/)



* Ferramentas para trabalhar com MySql:
	* Sequelize (ORB tipo o Hibernate)

* Ferramentas para ter a visão gráfica das tabelas com MySQL:
 	* MySQL Workbrench
 	* HeidiSql
 	* Navicat

## Git

 ### Para fazer um commit de qualquer alteração:
1. Para criar e já mudar para o branch: 
	``` 
	git checkout -b bugfix/1361
	``` 
2. Remover os arquivos alterados indesejados:
	``` 
	git checkout -- pom.xml
	git checkout -- "java/impl/PlatformBackendServer.java" 
	```
3. Adicionar os arquivos alterados:
	``` 
	git add .
	``` 
4. Efetuar o commit:
	``` 
	git commit -m "#APG-1361 - Removido verificação de permissão não necessária"
	``` 
5. Efetuar o push:
	``` 
	git push -u origin bugfix/apg-1361
	``` 	

 * Para ver todos os branches locais:
	**git branch --list**

 * Para ver todos os branches remotos:
	**git branch -r**

 * For delete a local branch:
	**git branch -d + name_local_branch**
	
 * For change the name of the local branch:
	**git branch -m new_name**
	
 * For create a new tag:
	**git tag -a V1.0 -m "my version 1.0"** <br>
	**git push origin --tags**


## Java

### Atalhos:
* **CTRL + SHIFT + O:** para importar bibliotecas
* **F4 ou Ctrl + Alt + G:** abre as referencias da classes, método ou propriedade (como o Shift + F12 do visual studio)
* **Ctrl + Shift + R:** como o Ctrl + , do Visual Studio
* **F3:** vai até a implemetação do método/variável
* **Ctrl + H:** para pesquisar qualquer texto dentro de qualquer fonte
* **Ctrl + Shift + H:** para pesquisar qualquer arquivo fonte dentro do workspace
* **Ctrl+Alt+H:** (é necessário estar no modo de visualização: Java EE) > pesquisa no workspace por todas as ocorrências do elemento sobre o qual o cursor está posicionado.
* **Ctls+Shift+O:** add imports

## Gerais

  * Para não precisar reiniciar o servidor de aplicação a cada alteração pode-se usar o [Nodemon](https://nodemon.io/)
 
## IIS
 * Reiniciar IIS: iisreset

### Proxy
 * Opções da Internet -> Conexões -> Configurações da LAN <br>
Marcado para "Não usar servidor proxy para endereços locais".

### Portas utilizadas
 * No cmd: netstat -a

 ## Oracle

 ### Como ver conexões ativas:
```
SELECT SID, Serial#, UserName, Status, SchemaName, Logon_Time
FROM V$Session
WHERE 
Status='ACTIVE' AND
UserName IS NOT NULL;
```

### How to create a sequence in oracle
```
create sequence TESTE_SEQ
minvalue 1
maxvalue 9999999999
start with 1
increment by 1
nocache
cycle;
```

**Where:**
* minvalue = Valor minimo
* max value = valor máximo que poderá chegar
* start with = valor inicial
* increment by 1 = (incremento), se este valor for 2, a sequence será incrementada como; 1,3,5,7,…
* CYCLE = Sequencia será recomeçada ao atingir o valor maximo
* NO CYCLE = default
* OWNED BY table.col = Associa a uma coluna
* OWNED BY NONE = sem associação

### How to increment sequence
```
SELECT TESTE_SEQ.Nextval
-- Caso for testar no PL-SQL ou outro programa acrescente um from dual para obter o resultado.
SELECT TESTE_SEQ.Nextval FROM DUAL
```

# Windows

## Generals

### Excluir serviços do windows
 * Run the CMD as an administrator
 ```
 sc delete <service's name>
 ```
 
## Certificado digital

### É possível alterar a senha de certificados digitais do tipo A1 da seguinte forma:
 * Importar o certificado marcando a opção: "Marcar essa chave como exportável".
 * Abrir o WIN + R: MMC <enter>
 * No menu Arquivo, clique em Adicionar/Remover Snap In. Clique em Adicionar.
 * Pessoal > Certificados (localizar o certificado desejado)
 * Botão direito > Todas as tarefas > Exportar > Sim, exportar a chave privada 
 * Marcar as opções: 
 	* Incluir todos os certificados no caminho de certificação, se possível
 	* Exportar todas as propriedades estendidas
 * Avançar > Informar a nova senha
 * Definir um local para salvar e o nome do arquivo 


 