Projeto  ImportaCSV 

Para efetuar o teste do Projeto em seu servidor local, faça o seguinte procedimento 
1 -  Em seu Diretório raiz “C:\” crie uma pasta chamada Arquivos , copie o arquivo Vendas.txt existente no repositório do projeto para esta pasta.  
2 -  Entre no SQL Server 2014 Management Studio e crie o Banco de Dados WPRD_VENDAS, com o banco criado entre na Opção -> Consulta do Mecanismo de Banco de Dados banco  e execute o Script abaixo  para criar a tabela VENDAS:
USE WPRD_VENDAS

IF NOT (EXISTS (SELECT * 
                 		FROM INFORMATION_SCHEMA.TABLES 
                 	        WHERE TABLE_SCHEMA = 'WPRD_VENDAS' 
                                   AND TABLE_NAME = 'VENDAS'))				        
BEGIN        
CREATE TABLE VENDAS
		(
			IdVenda    		 INT	NOT NULL	PRIMARY KEY,	
			DtaVenda  		Date	NOT NULL,
			IdCliente		INT	NOT NULL, 
			NomeCliente     	VARCHAR(100)	NOT NULL,
			VlrVenda            	DECIMAL(18,2)	NOT NULL			
		)
END

Observação a tabela VENDAS foi criada com base na estrutura do Arquivo Vendas.txt

3 = Caso queira fazer o teste com sua Base de Dados será necessário efetuar as seguintes   alterações no código fonte do Projeto , para isso Acesse o Visual Studio e altere o código da instrução  ConnectionString  existente na classe Default.aspx.cs para : 

ConnectionString = @"DataSource=SEU SERVIDOR;Initial Catalog=SEU BANCO; Integrated                Security=True"
Os passos acima descritos são requisitos para que o teste seja bem sucedido.
 

