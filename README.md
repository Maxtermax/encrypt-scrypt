=======
Enigma-code 
==============

![alt tag](http://www.enigma-replica.com/LampPanel/NewLampFilmEnigma6Web.jpg)

=======
Que es enigma-code ?
==============


Es un sencillo modulo hecho en el framework de javascript node.js que sirve para encriptar contraseñas con varias funciones para comparar, desencriptar etc.

=======
Ejemplo ?
==============
 Claro puedes correr un pequeño ejemplo y ver la magia este modulo para hacer esto sigue los siguientes pasos:

## 1- npm install enigma-code
Este comando instala el modulo.

## Como saber si instalo bien ?

ejecuta el comando: npm start \n
si vez un mensaje que dice ENIGMA-CODE  
significa que todo se instalo correcta mente de lo contrario
intenta de nuevo.


## 2- Ubicar ejemplo
Ubicate en el folder donde esta el ejemplo de enigma-code

cd example 

##3- node example
Despues de que esto puedes correr el ejemplo  con:

node example.js


=======
Como usar ?
==============
Es bastante facil ya que no son muchas las funciones que tiene enigma-code puntualmente funciona de la siguiente forma:

## Primera funcion Generar hash:


```javascript
var enigma=require('enigma-code')//llama el modulo 

var valorEncriptacion=10;//puede ser cualquier numero
enigma.genHash(valorEncriptacion)//genera el hash de tu contraseña
//teniendo como base el valor de encriptacion 
//que le pases como parametro es de tu eleccion en valor que le pases

var key='millave';//No debe tener espacios

enigma.genHash(valorEncriptacion,key)
/*El segundo parametro es una llave o key esto es una vale de seguridad 
con el cual todas tus contraseñas seran encriptadas
sin esto sera imposible desencriptar con exito la longitud de esta llave
debe ser inferior a 10 caractes, pero si quieres tambien puedes encriptar
esta llave.
*/
```

Es importante dejar en claro que cada contraseña que encriptes
con el valor que tenga tu key solo podra ser desencriptada con 
exito si el key es el mismo con el que fue encriptada la contraseña.

```javascript

enigma.genHash(valorEncriptacion,key,'contraseña123')
/*
El tercer parametro es la contraseña en texto plano que te interesa encriptar
esta contraseña debe ser validada con una exprecion regular
de contraseñas que acepte minimo 10 caracteres y maximo 15 o mas 
por el lado del frontend puedes usar esta por ejemplo:
	var Reg=new RegExp(/^[a-zA-Z0-9ñ]{10,15}$/).test('min10caracteres');//true
*/
	
```
Puedes aprender mas sobre expreciones regulares aqui: http://webintenta.com/validacion-con-expresiones-regulares-y-javascript.html

```javascript


enigma.genHash(valorEncriptacion,key,'contraseña123',function(err,hash){
	if(err) return console.log(err);//Solo se ejecutara si existe un error
	console.log(hash)//2dl3lkwkj13kj12k12kj321kj
//esa funcion retorna por defecto en hash la contraseña encriptada

});//el cuarto paramtro es una funcion que tiene con parametros un error en caso tal de
//que ocurriera un error y el segundo parametro que devuelve es el 'hash' 
//es decir la contraseña encriptada es importante pedirlo en el callback de la funcion

//eso es todo con la funcion de encriptar contraseña o genHash() :)
```

## Segunda funcion Desencriptar hash:
Esta funcion es muy sencilla de usar es importante dejar claro que primero se debe establecer.

El valor de encriptacion con la funcion genHash() 
es decir la funcion genHash() siempre debe ir declarada primero


```javascript


var hash='ē285ĺ324ķ321Ĭ310ķ321ĺ324ĳ317Ĵ318Į312Ĵ318ľ328Ŀ329İ314';

enigma.Desencriptar(hash)//el primer parametro que se necesita
//en esta funcion es obviamente la hash a desencriptar

//si el valor de encriptacion es distinto al el valor con el que esta encriptado 
//el hash entonces desencriptara mal.

enigma.Desencriptar(hash,function(err,des){
	if(err) return console.log(err);
	console.log(des);//return desencriptacion
});//el segundo parametro es una funcion que tiene con parametros un error en
 //caso tal de que ocurriera un error y el segundo parametro que devuelve es 'des'
// es decir la contraseña desencriptada

/*
importante dejar claro que el valor de encriptacion de el hash
con el que se quiere  debe ser igual al que se definio en la funcion
genHash() y tambien el valor de el 
key  de lo contrario no podra desencriptar con exito
muy similar a la funcion anterior.
*/ 

```

## Tercera funcion Comparar:
Esta funcion retorna un valor boolean si la contraseña candidata 
es la misma del hash entonces retornara true de lo contrario false.

```javascript

var hash='ē285ĺ324ķ321Ĭ310ķ321ĺ324ĳ317Ĵ318Į312Ĵ318ľ328Ŀ329İ314';

enigma.comparar(hash)//el primer parametro es el hash que deberia estar en tu
//DB store encriptado con la funcion genHash()

enigma.comparar(hash,'ContraseñaCandidata')//el segundo parametro es la contraseña candidata con la que se intenta validar

enigma.comparar(hash,'ContraseñaCandidata',function(res){
	console.log(res)//false
});//el tercer parametro es una funcion que tiene con parametros un error en
 //caso tal de que ocurriera un error y el segundo parametro que devuelve es 'res'
// es decir la respuesta de si la contraseña candidata es igual a el hash o no 
//'res' es un valor boolean que retorna true o false



/*
Importante dejar claro que el valor de encriptacion de el hash que se quiere compara 
debe ser igual al que se definio en la funcion genHash() y tambien el valor de el 
key  de lo contrario no podra comparar se con exito
*/
```



=======
Errores:
==============

## "Antes de comparar necesita un valor de encriptacion"

```
Es por que no haz definido el valor de encriptacion con la funcion 
genHash() si no sabes cual esta funcion:ve hacia la seccion como usar enigma y busca 
la primera funcion de todas llamada "funcion Generar hash"
```
## "Antes de Desenciptar necesita un valor de encriptacion"
```

Es por que no haz definido el valor de encriptacion con la funcion genHash() 
si no sabes cual esta funcion

ve hacia la seccion como usar enigma y busca la funcion principal
llamada "funcion Generar hash".
```

## "Error introduce un valor mayor a cero"

```
Este error se produce por que le pasaste como parametro a la funcion genHash()
un valor no valido como lo es 0 o inferior es decir valores negativo
```

## "Error introduce un valor mayor a cero"

```
Este error se produce por que le pasaste como parametro a la funcion genHash()
un valor no valido como lo es 0 o inferior es decir valores negativo
```


## "Error Introduce una contraseña valida"
```
Este error se produce por que en la funcion genHash() esta especificado que el 
parametro de la contraseña debe ser de minimo 10 caracteres y maximo 15 y sin espacios
para solucionar lo solo tienes que cumplir las reglas anterios mente mencionadas
puedes usar una exprecion regular tambien te recomiendo que sigas este tutorial 
si no conoces bien las expreciones regulares: http://webintenta.com/validacion-con-expresiones-regulares-y-javascript.html 
```
## "Contraseña erronea"
```
Este error se produce cuando intentas desencriptar o compara una contraseña 
con el key o llave incorrecto con esto me refiero a que el key con el cual 
fue encriptada la contraseña originalmente es distinto al que definiste en la funcion genHash(), para solucionarlo debes introducir el key correcto.

```




##Autor :Esneyder Amin Palacios Mena   https://www.facebook.com/esnene02
##Contacto:
##	1- esneyder_a@hotmail.com 
##  2- esnene02@gmail.com 
##  3- https://twitter.com/Sneyder_A 
##From @Quibdojs  		 								 https://twitter.com/QuibdoJs
##Github:https://github.com/Maxtermax