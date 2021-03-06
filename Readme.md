### Para acessar o [projeto](https://curso-node1.herokuapp.com/)

# Databases

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

## SQL Server
 
 ### Como alterar as propriedades da instância 
 Caso não estiver conseguindo logar no sql server com o usuário 'sa' pode ser por que a instancia está configurada para apenas autenticação do windows. Para corrigir isso, logar com autenticação windows e depois clicar com botão direito sobre a instancia '.\sqlexpress' (ou outra) -> Propriedades -> Segurança -> Selecionar: Modo de autenticação do Sql Server e do windows
 
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

### How to create user oracle
* Open CMD
* lsnrctl status 
* sqlplus sys/12345678 as sysdba
* create user < name user > identified by < pwd user >;
* grant dba to < name user >;

### Backup
#### How to create a dump
```
exp usuario_backup/senha@banco file=c:\base.dmp log=c:\base.log
```
#### How to import a dump
```
imp usuario_destino_restore/senha@banco file=c:\base.dmp log=c:\base.log commit=y fromuser=usuario_backup touser=usuario_destino_restore
```
**ex:**
```
imp sdefelipelocal/sdefelipelocal@xe file=C:\Publica\base_Felipe\bkp581011.DMP log=C:\Publica\base_Felipe\base.log commit=y fromuser=sdenew10 touser=sdefelipelocal
```

## Gerais

  * Para não precisar reiniciar o servidor de aplicação a cada alteração pode-se usar o [Nodemon](https://nodemon.io/)

# Git

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

 * Para ver as mudanças de um arquivo por vez:
	**git diff arquivo.txt**

 * For delete a local branch:
	**git branch -d + name_local_branch**
	
 * For change the name of the local branch:
	**git branch -m new_name**
	
 * For create a new TAG:
	**git tag -a V1.0 -m "my version 1.0"** <br>
	**git push origin --tags**


# Languages
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
 
## IONIC

### Tips
* **To see all devices connected on USB:** adb devices
* **To run app on device (target=your device`s id):** ionic cordova run android -lcs --device --target=0039936300
* **To add Platform Android in project:** ionic cordova platform add android --save
* **To create a page automatically:** ionic generate page my-page-name
* **To create a component:** ionic generate component my-component-name

### Publishing your app
* **To do a build to generate an .apk:** ```ionic cordova build --release android```
* **Or:** ```ionic cordova build android --release --prod```
* **Necessário rodar todos os comandos na raiz do projeto. Trazer o .apk pra raiz pra rodar o segundo comando:**
* **Gerar keystore:** ```keytool -genkey -v -keystore my-release-key.keystore -alias ksapp -keyalg RSA -keysize 2048 -validity 10000```
* **Assinar apk:** ```jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore app-release-unsigned.apk ksapp```
* **Zipar apk (foi necessário trazer o zipalign.exe para a pasta raíz do projeto para poder rodar este comando):** ```./zipalign -v 4 app-release-unsigned.apk ksapp.apk```

* **Após isso, teremos o ksapp.apk pronto para ser adicionado na google play**
 
### Lifecycle events
**ionViewWillEnter: void**
É executado quando a página está prestes a entrar e se tornar a pagina ativa.

**ionViewDidEnter: void**
É executado quando a página foi totalmente inserida e é agora a pagina ativa. Este exento irá disparar se for a primeira chamada ou se a pagina estiver em cache.

**ionViewWillLeave: void**
Executa quando a página está prestes a sair e deixar de ser a pagina ativa.

**ionViewDidLeave: void**
Executa quando a página terminou de sair e já não é mais a pagina ativa.

**ionViewWillUnload: void**
Executa quando a página está prestes a ser destruida e seus elementos removidos. Ou seja, logo após o ionViewDidLeave.

**ionViewCanEnter: boolean / Promise <void>**
É executado antes da view/página poder entrar. Isso pode ser usado como uma espécie de "guarda" em páginas autenticadas em que voce precisa verificar se o usuário tem permissao de acesso.

**ionViewCanLeave: boolean / Promise <void>**
É executado antes da view/página poder sair. Isso pode ser usado como uma espécie de "guarda" nas páginas em que voce precisa verificar se as informações foram salvas por exemplo, ou para fazer logoff do usuário.

### Executar aplicacoes em todos os dispositivos com layout de android/ios:
No arquivo **app.module.js** no codigo Imports[] um novo parametro, ex: 
	``` 
	imports: [
		IonicModule.forRoot(MyApp, {
			mode: 'md' //para android
			mode: 'ios' //para ios
		})
		]
    ```

### Para verificar o service worker (cache) do chrome:
**chrome://serviceworker-internals/**

# Windows

## Generals

### Excluir serviços do windows
 * Run the CMD as an administrator
 ```
 sc delete <service's name>
 ```

## IIS
 * Reiniciar IIS (CMD): iisreset

### Proxy
 * Opções da Internet -> Conexões -> Configurações da LAN <br>
Marcado para "Não usar servidor proxy para endereços locais".

### Portas utilizadas
 * No cmd: netstat -a

 
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

### Tips
 * **Keyboard shortcut to duplicate a line:** Shift + Alt + ↓(on keyboard)

 