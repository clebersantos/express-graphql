## Estudos de ExpressJs e GraphQL

### Para executar

```
node server2.js
```

acessar localhost:4000/graphql

Exemplo para obter um curso na interface gráfica

```
{
  course(id:3) {
    id,
    title
  }
}
```

Exemplo para obter a lista
```
{
  courses {
    id,
    title
  }
}
```

Exemplo para definir uma query

```
query getSingleCourse($courseID: Int!) {
  course(id: $courseID) {
    title
    author
    description
    topic
    url
  }
}
```

Para obter o resultado da query acima insira o código abaixo em `Query Variables`

```
{
  "courseID1": 1,
}
```

 Exemplo com fragmentos

 ```
 query getCourseWithFragments($courseID1: Int!, $courseID2: Int!) {
	      course1: course(id: $courseID1) {
	             ...courseFields
	      },
	      course2: course(id: $courseID2) {
	            ...courseFields
	      } 
	}

	fragment courseFields on Course {
	  title
	  author
	  description
	  topic
	  url
	}
```

Para obter o resultado da query acima insira o código abaixo em `Query Variables`

```
{
  "courseID1": 1,
  "courseID2": 2
}
```

Exemplo de mutation

```
mutation updateCourseTopic($id: Int!, $topic: String!) {
  updateCourseTopic(id: $id, topic: $topic) {
    ... courseFields
  }
}
```

Para executar a mutation insira o código abaixo em `Query Variables`

```
{
  "id": 1,
  "topic": "JavaScript"
}
```