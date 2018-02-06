# MongoDB - Atividades para fixação do conteúdo 



## Instalação do MongoDB
   - Instale o MongoDB
   - Execute no terminal mongod (servidor)
   - Execute o mongo (MongoDB)

## 1) Crie um banco de dados chamado biblioteca
 
 ```
 use biblioteca
 ```

## 2) Crie uma coleção (collection) chamada livros

```
 db.createCollection('livros')
```

## 3) Crie os seguintes documentos:

  - título: Introdução a linguagem de marcação HTML
  - valor: 25.00
  - autor: João



   - título: NodeJS do básico ao avançado
   - valor: 280.00
   - autor: Jorge



   - título: Android - criando apps reais
   - valor: 290.00
   - autor: Jamilton



  - título: PHP e MySQL
  - valor: 190.00
  - autor: Fernando



  - título: Lógica de Programação
  - valor: 20.00
  - autor: Maria

```
 db.livros.save(
	{
		titulo: 'Introdução a linguagem de marcação HTML',
		valor: 25.00,
		autor: 'João'
	}
)

 db.livros.save(
	{
		titulo: 'NodeJS do básico ao avançado',
		valor: 280.00,
		autor: 'Jorge'
	}
)

 db.livros.save(
	{
		titulo:'Android - criando apps reais',
		valor: 290.00,
		autor: 'Jamilton',
	}
)

 db.livros.save(
	{
		titulo:'PHP e MYSQL',
		valor:190.00,
		autor: 'Fernando',
	}
}
	
 db.livros.save(
	{
		titulo:'Lógica de Programação',
		valor:20.00,
		autor: 'Maria'
	}
)
```

## 4) Crie as seguintes consultas:

 Crie uma consulta que retorne apenas os documentos de livros com valores superiores a 200.00

 ```
 db.livros.find(
	{
		valor : {$gt : 200.00}
	}
 ).pretty()
```

 Crie uma consulta que retorne apenas os documentos com valores entre 10 e 30
	
```	
 db.livros.find(
	{
		valor : {$gte : 10.00},
		valor : {$lte : 30.00}
	}
 ).pretty()
```

 Crie uma consulta que retorne todos os documentos, executo aqueles cujo autor seja Fernando

```
 db.livros.update(
	{
		autor:{$ne : 'Fernando'}
	}
 ).pretty()
```


## 5) Atualize os seguintes documentos:

 Atualize o documento cujo o título é PHP e MySQL, passando seu valor de 190.00 para 175.00

```
 db.livros.update(
	{ 
		titulo:{ $eq: "PHP e MYSQL" }
	}
	,
	{
		$set: {
			valor: 175.00
		}
	},
	{
		multi: true
	}
 )
```

 Atualize o documento cujo autor é Jorge, passando seu título para Curso Completo de NodeJS

```
 db.livros.update(
 {
	autor: {$eq : 'Jorge'}
 },
 {
	$set: {titulo:'Curso Completo de NodeJS', autor: 'Jorge Santana'}
 },
 {
	multi: true
 }
 )
```

 Atualize todos os documentos cujo valor são iguais ou inferiores a 25.00 para o valor 27.00

```
 db.livros.update(
	{
		valor:{$lte: 25}
	},
	{
		$set:{ valor: 27}
	},
	{
		multi: true
	}
 )
```

## 6) Remove os seguintes documentos:

 Remova o documento cujo autor é João

```
 db.livros.remove(
	{ autor: 'João'},
	true
 )
```

 Remova todos os documentos cujo valor é superior a 280.00

```
 db.livros.remove(
	{valor: {$gt: 280}}, true
 )
 ```

 Remova todos os documentos cujo valor é inferior a 30.00

 ```
 db.livros.remove(
	{ valor: {$lt: 30}}
	, true
 )
 ```