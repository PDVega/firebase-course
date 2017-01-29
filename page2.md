# ![Firebase logo](imgs/firebase.png) Firebase
##Realtime Database

Primero, para modificar la base de datos debemos ir a **Database** → **Rules** y definir las siguientes reglas (solo para desarrollo)
~~~
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
~~~

Para crear una **referencia** a la base de datos usamos

	var dbRef = firebase.database().ref();
	
Crear un **hijo** en la referencia raíz llamado **object** es tan simple como

	const dbStudent = dbRef.child('student');

si usamos la función **set** para poner/reemplazar valores en la base de datos
~~~
dbStudent.set({
	name: 'Juan',
	lastname: 'Escutia',
	age: 20
});
~~~

la base de datos quedaría así
~~~
awesomeproject {
	student {
		age: 20,
		lastname: 'Escutia',
		name: 'Juan'
	}
}
~~~

La función **on** escucha los cambios en la referencia de la base de datos especificada, y se utiliza de la siguiente forma
~~~
dbStudent.on('value', function(snapshot) {
	console.log( snapshot.val() );
}
~~~
	
Cuando no necesitamos escuchar cambios del servidor utilizamos la función **once**
~~~
dbStudent.once('value', function(snapshot) {
	console.log( snapshot.val() );
}
~~~

Cuando requerimos trabajar con listas de datos, es decir, eventos ocurriendo en los hijos de una referencia, en vez de usar **'value'**, usaremos alguno de los siguientes ejemplos dependiendo del caso de uso 
~~~
dbStudent.on('child_added' function(snapshot){ 
	//some code
});
~~~

| Evento 			| Caso de uso |
| :-------------:		| :------ |
| child_added		| lorem ipsum dolor sit amet bla bla 	|
| child_changed	| lorem ipsum dolor sit amet bla bla 	|
| child_removed	| lorem ipsum dolor sit amet bla bla 	|
| child_moved		| lorem ipsum dolor sit amet bla bla 	|

## [Anterior](page1.md) - - [Siguiente](page3.md)
