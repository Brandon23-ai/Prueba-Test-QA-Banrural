# Resolucion de problemas

1. Sintaxis "addeventListener": 

    - Error:  Sintaxis incorrecta en el metodo "addeventListener"
     **guessSubmit.addeventListener('click', checkGuess);**.
     **resetButton.addeventListener('click', resetGame);**

    - Solucion: Corregir la letra E mayuscula "addEventListener" y modificar las lineas de codigo que utilicen el metodo "addEventListener".
     **guessSubmit.addEventListener('click', checkGuess);**
    **resetButton.addEventListener('click', resetGame);**


2. Sintaxis "'lowOrHi'"

    - Error: Sintaxis incorrecta  en 'lowOrHi'
    **const lowOrHi = document.querySelector('lowOrHi');**

    - Solucion: Debe llevar "." al inicio ya que es una clase de html
     **const lowOrHi = document.querySelector('.lowOrHi')** 
    

3. Objeto Math.random():

    - Error: Math.random(), devuelve un número de coma flotante aleatorio de 0 a menor que 1 incluyendo decimales
    **let randomNumber = Math.random() * 10;**. 

    - Solucion: Uso de Math.floor() que devuelve el máximo entero menor o igual a un número. Modificamos las lineas de codigo que hagan uso del objeto Math.
    **let randomNumber = Math.floor(Math.random() * 100) + 1;** 
    **randomNumber = Math.floor(Math.random() * 100) + 1;**
    

4. Tipo de valor de entrada en "userGuess":

    - Error: 
    **let userGuess = guessField.value;**

    - Solucion: Aseguramos de que la entrada de dato sea de tipo "Number" para prevenir fallas.  
    **let userGuess = Number(guessField.value)**
    

5. Orden de las condiciones: 

    - Error: La primera condicion nos dice que si el numero ingresado es igual al objeto random creado, da como salida "'!!!Pérdistes!!!'"; lo cual es erroneo. 

        "if(userGuess === randomNumber) {
            lastResult.textContent = '!!!Pérdistes!!!';
            lastResult.style.backgroundColor = 'black';
            lowOrHi.textContent = '';
            setGameOver();
        } else if(guessCount === ATTEMPS) {
            lastResult.textContent = 'Felicitaciones! adivinaste el número!';
            lastResult.style.backgroundColor = 'red';
            setGameOver();
        } else {
            lastResult.textContent = 'Incorrecto! ';
            lastResult.style.backgroundColor = 'green';
        if(userGuess < randomNumber) {
            lowOrHi.textContent = 'El número es mayor!';
        } else if(userGuess > randomNumber) {
            lowOrHi.textContent = 'El número es menor!';
        }
        }"

    - Solucion: Cambiamos el texto de salida a "'Felicitaciones! adivinaste el número!'".

        if(userGuess === randomNumber) {
            lastResult.textContent = 'Felicitaciones! adivinaste el número!'; 
            lastResult.style.backgroundColor = 'Green';
            lowOrHi.textContent = '';
            setGameOver();
        } else if(guessCount === ATTEMPS) {
            lastResult.textContent = '!!!Pérdistes!!!';
            lastResult.style.backgroundColor = 'red';
            setGameOver();
        } else {
            lastResult.textContent = 'Incorrecto! ';
            lastResult.style.backgroundColor = 'black';
        if(userGuess < randomNumber) {
            lowOrHi.textContent = 'El número es mayor!';
        } else if(userGuess > randomNumber) {
            lowOrHi.textContent = 'El número es menor!';
        }
        }


6. Planteamento de la logica de negocios:

    - Error: El color de los textos no coindicen con el planteamiento del programa.

        "if(userGuess === randomNumber) {
            lastResult.textContent = '!!!Pérdistes!!!';
            lastResult.style.backgroundColor = 'black';
            lowOrHi.textContent = '';
            setGameOver();
        } else if(guessCount === ATTEMPS) {
            lastResult.textContent = 'Felicitaciones! adivinaste el número!';
            lastResult.style.backgroundColor = 'red';
            setGameOver();
        } else {
            lastResult.textContent = 'Incorrecto! ';
            lastResult.style.backgroundColor = 'green';
        if(userGuess < randomNumber) {
            lowOrHi.textContent = 'El número es mayor!';
        } else if(userGuess > randomNumber) {
            lowOrHi.textContent = 'El número es menor!';
        }
        }"

    - Solucion: Corregimos el orden de los colores de texto

        if(userGuess === randomNumber) {
            lastResult.textContent = 'Felicitaciones! adivinaste el número!'; 
            lastResult.style.backgroundColor = 'Green';
            lowOrHi.textContent = '';
            setGameOver();
        } else if(guessCount === ATTEMPS) {
            lastResult.textContent = '!!!Pérdistes!!!';
            lastResult.style.backgroundColor = 'red';
            setGameOver();
        } else {
            lastResult.textContent = 'Incorrecto! ';
            lastResult.style.backgroundColor = 'black';
        if(userGuess < randomNumber) {
            lowOrHi.textContent = 'El número es mayor!';
        } else if(userGuess > randomNumber) {
            lowOrHi.textContent = 'El número es menor!';
        }
        }


7. No. de intentos:

    - Error: Variable para numero de intentos inicia en 5.
    **const ATTEMPS = 5;**

    - Solucion: Iniciar variable para numero de intentos en 10.
    **const ATTEMPS = 10;**


8. Contador de intentos:

    - Error: Contador inicia en 1 dando un total de 9 intentos.

        if(guessCount === 0) { //el contador tiene que inicar en 0
            guesses.textContent = 'Número aleatorio anterior: ';
        }
    
    - Solucion: Iniciar el contador en 0 para hacer un total de 10 intentos.

        if(guessCount === 0) { 
            guesses.textContent = 'Número aleatorio anterior: ';
        }


9. Alerta para ingresar datos enteros:

    - Problema: El programa no cumple con la logica de negocio planteada.

    - Solucion: Implementamos una condicion para que el usuario ingrese unicamente datos enteros.

        if (!Number.isInteger(userGuess)) {
            lastResult.textContent = "Ingresa un entero";
            lastResult.style.backgroundColor = "orange";
            guessField.value = '';
            guessField.focus();
             return;
        }

10. Alerta para ingresar valores que se encuentren en el rango establecido:

    - Problema: El programa no cumple con la logica de negocio planteada.

    - Solucion: Implementamos una condicion que permita que el usuario ingrese valores en el rango establecido. 

        if ( userGuess > 100) {
            lastResult.textContent = "Ingresa un valor entre 1 y 100";
            lastResult.style.backgroundColor = "orange";
            guessField.value = '';
            guessField.focus();
            return;
        }



//Para poder testear el programa se agrego la visualizacion del numero aleatorio generado y asi poder ingresarlo y verificar que se cumpla lo requerido. 
//Dicho valor puede ser visualizado en la consola del navegador web.



    



