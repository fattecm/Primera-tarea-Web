Primera-tarea-Web
=================

Solo números primos         Solo valores hexadecimales         Número de cedula correcto      Crear las siguientes funciones que reciban 2 parámetros         Suma de parámetros siendo estos números binarios         Invertir texto del segundo parámetro encontrado en el primero     Desarrollar totalmente en JavaScript una factura con los siguientes requerimientos:         Ubicar los productos en un arreglo y permitir una búsqueda por índice desde la factura         Ubicar los clientes en un arreglo y permitir una búsqueda por índice desde la factura         Permitir ingresar N productos a la factura de manera dinámica         Sistemáticamente debe ir acumulando la suma de los productos, así como el IVA y el descuento al final de la factura

<!DOCTYPE html>
<!--
Esta página va a indicar si el dato introducido es primo, o no primo.
-->
<html>
    <head>
        <title>Primo o No Primo</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <h1><center>Verificación de número primo</center></h1>
    </head>
    <body>
     
         <div id="divContenido"> </div>
         <h3>Ingrese un número para comprobar si es primo </h3>
        <!-- insertamos un cuadro tipo texto para introducir el dato a validar -->
        <input type="text" id="txtdato" name="txtdato" /> 
        <!-- insertamos un boton para llamar a la función -->
        <input type="button" name="btn_verificar" id="btn_verificar" value="Obtener Resultado" onClick="esPrimoMio()" />
        <!-- Otro cuadro tipo texto, para mostrar el mensaje si es primo o no -->
        <br/>Resultado <input type="text" name="resultado" id="resultado"/>
    </body>
    <footer>
			<small>
                            <br/>
                            <br/>
                            <br/>
				Documento realizado 27 de Abril del 2014 <br/>
				Autor Fátima Carrillo Morán
			</small>
    </footer>
</html>
<!-- Scritp q cmprueba si un numero es primo, es decir si es divisible
por uno y por si mismo unicamente -->

<script>
function esPrimoMio()
{
    var dato="";
    //guardamos en la variable dato, lo que se haya introducido en txtdato
    dato=document.getElementById("txtdato").value;
    //convertimos dato a entero
    dato=parseInt(dato);
    //declaramos e inicializamos la varible divisores, para ir guardando cuantas
    //veces se divide el dato 
    var divisores = 2;
    for ( j = 2; j<dato ; j++){
        if (dato%j == 0){
        divisores++;
        break;
        }
    }
    //Si divisores=2, quiere decir que si es primo, ya que se divide por si mismo
    // y por la unidad
    if (divisores == 2){
        document.getElementById('resultado').value = 'ES primo';
    //caso contrario no es primo
    }else{
            document.getElementById('resultado').value = 'NO es primo';
         }
}

</script>

<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>Validación de Hexadecimal</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <div>Introduce número para su validación en Hexadecimal</div>
        
            <input type="text" id="txtValor" name="txtValor" 
                   onblur="if(valHexadecimal(this.value)) 
                       alert('El número introducido SI es Hexadecimal'); 
                       else alert ('El número introducido NO es Hexadecimal')">
            <input type="button" id="butValor" name="butValor" value="Verificar"
                   onclick="valHexadecimal(document.getElementById('txtValor').value)">
        
    </body>
    <footer>
			<small>
                            <br/>
                            <br/>
                            <br/>
				Documento realizado 01 de Mayo del 2014 <br/>
				Autor Fátima Carrillo Morán
			</small>
    </footer>
</html>

<script>
    function valHexadecimal(valor){
        var esHexad="1";
        //var hexaValor=["A","B","C","D","E","F","a","b","c","d","e","f","0","1","2","3","4","5","6","7","8","9"];
            /*for (i = 0; i <valor.length; i++) {
                var caracter = valor.charAt(i);
                alert("caracter"+ caracter
                alert("valores hexade"+ hexaValor);
                for (j = 0; j <22; j++) {
                    if(caracter==hexaValor[j])
                       esHexad="1";
                    else
                        esHexad="0";                      
                }
    
            }*/
            for (i=0; i<valor.length; i++){
            var caracter=valor;
            //var caracter = valor.charAt(i);
            //var caracter = valor.substring(i,i+1);
            if((caracter>="0" && caracter<="9")||(caracter=="A" || caracter=="B" ||
                    caracter=="C" || caracter=="D"
                    || caracter=="E" || caracter=="F")){
                //alert("caracter" +caracter);
                esHexad="1";
            }else{
            esHexad="0";
            }
        }
        if(esHexad=="0")
            return false;
        else
            return true;
        
    }
</script>

<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html lang="es">
    <head>
    <meta charset="utf-8" />
    <title>Cédula</title>
    <h1><center>Introduce el número cédula</center></h1>
    </head>
    <form id="frmdata" name="frmdata"/>
    Cedula:<input type="text" name="cedula"  id="cedula"/>
    <input type="button" id="botonValidar" name="botonValidar"  value="Validar" onclick="validarCedula(document.forms[0].cedula.value)" />
    </form>
</body>
</html>
    <script>
        /*Esta es una funcion para verificar la cedula en el checkbox de lapagina*/
        function validarCedula( form )
        {
            var cedula = form;
            arrayCedula = cedula.split( "" );
            var num = arrayCedula.length;
            //alert("tamaño cedula"+num)
            if ( num == 10 )
            {
                
                var totalImpar=0;
                var UltimoDigito = (arrayCedula[9]);
                var totalPar = 0;
                //alert("El ultimo digito"+UltimoDigito);
                for( i=0; i < (num-1); i++ )//se opera con todos menos con el ultimo digito
                {
                  var mult = 0;
                  if ( ( i%2 ) != 0 ) { //Si es par la posición, empezando de 1, no de 0
                    
                    var totalPar = totalPar + ( arrayCedula[i] *1); 
                    //alert("total par" + totalPar);
                  }
                  else // es impar la posicion empezando por 1, se multiplica *2
                  {
                    mult = arrayCedula[i] * 2;
                    //alert("multiplicacion es"+mult);
                        if ( mult > 9 ){ //si la multiplicación resulta mas de 9, se resta 9
                          totalImpar = parseInt(totalImpar + ( mult - 9 ));
                          //alert("total sin 9"+totalImpar);
                        }else{
                            totalImpar = parseInt(totalImpar + mult);
                        }
                  }
                  //alert("total Impar"+totalImpar);
                  //alert("total Par"+totalPar);
                }
                var Total= parseInt(totalPar + totalImpar);
                decena = Total / 10;
                //alert("el Total es "+ Total);
                decena = Math.floor( decena );//coge solo el entero
                //alert("la decena es "+ decena);
                decena = ( decena + 1 ) * 10;
                //alert("la decena es "+ decena);
                final = ( decena - Total );
                //alert("el último digito es  "+ final);
                if ( ( final == 10 && UltimoDigito == 0 ) || ( final == UltimoDigito ) ) {
                  alert( "El número de cédula es correcto" );
                  return true;
                }
                else
                {
                  if(final==10)
                      final=10-10;
                  
                  alert( "Número de cédula incorrecto, último digito debe ser: " +final );
                  return false;
                  
                }
            }
            else
            {
              alert("Digitos de cédula incorrecta, verifique nº de digitos");
              return false;
            }
          }
</script>
<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>Factura</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <div><center><h1>Factura</h1></center></div>
        Cliente: <input type="text" id="textClientes" name="texClientes"/>
        <input type="button" id="boton" name="boton" value="Buscar Cliente" 
               onclick="BuscarClientes(document.getElementById('textClientes').value)"/></br>
        <input type="text" id="producto" name="producto" size="80"/>
        
        <!--Colocamos tabla con encabezado y columnas <tr> indica la fila y <th> columna -->
        <table cellapacing="2">
            <thead>
                <tr>
                    <th>Cantidad</th>
                    <th>Productos</th>
                    <th>Precio Unidad</th>
                    <th>Precio Total</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td><input type="text" id="primer" name="primer"/></td>
                    <td><input type="text" id="primer2" name="primer2"
                               onblur="BuscarProductos(document.getElementById('primer2').value)"/></td>
                    <td><input type="text" id="primer3" name="primer3" /></td>
                    <td><input type="text" id="primer4" name="primer4" 
                               onblur="PrecioTotal(document.getElementById('primer').value, 
                                           document.getElementById('primer3').value)" /></td>
                   
                </tr>
                <tr>
                    <td><input type="text" id="segun" name="primer"/></td>
                    <td><input type="text" id="segun2" name="segun2"
                               onblur="BuscarProductos(document.getElementById('segun2').value)"/></td>
                    <td><input type="text" id="segun3" name="segun3" /></td>
                    <td><input type="text" id="segun4" name="segun4"
                               onblur="PrecioTotal(document.getElementById('segun').value,
                                   document.getElementById('segun3').value)"/></td>
                   
                </tr>
                
                 
            </tbody>
            
        </table>
        <table cellapacing="2">
            <thead>
                <tr><th>Total Cantidad: <input type="text" id="CantidadProducto" name="CantidadProducto"
                                               onblur="TotalCantidad()"/></th></tr></br>  
                <tr><th>Precio sin Iva: <input type="text" id="PrecioSinIva" name="PrecioSinIva"/></th></tr></br>
                <tr><th>Iva: <input type="text" id="iva" name="iva" /></th></tr></br>
                <tr><th>Precio: <input type="text" id="PrecioTotal" name="PrecioTotal" />  </th></tr></br>
                   <!--
                   
                   
                   -->          
            </thead>
            <tbody></tbody>
        </table>
        
        <div id="contenido"> </div>
    
    </body>
</html>

<script>
    
    function BuscarClientes(NombreCliente){
    var clientes=["Fátima Carrillo Morán   RUC: 130947803-8",
        "Magna Moran  RUC: 130947803-8","Leonardo Darquea  RUC: 130947803-8",
        "Arantxa Roa    RUC: 130947803-8"];
        //alert("cliente existe" + NombreCliente)
        //document.getElementById('producto').value = clientes[0];
        
    for (i = 0; i <clientes.length; i++) {
      var PrimeraLetraClient=NombreCliente.substring(i,i+1);
      var PrimeraLetraArray=clientes[i].substring(i,i+1)
        if (PrimeraLetraClient==PrimeraLetraArray){
            document.getElementById('producto').value = clientes[i];
            return;
        }else{
            alert("no dado de alta");
        }
    
    }
    //document.write(clientes[0]);
 }
 
 function GenerarTexto(n){
        var texto="";
        for (i = 0; i < n; i++) {
            texto+="<input type ='text' name='textos' /></br>"
        }
        document.getElementById("contenido").innerHTML=texto
    }
    
  function BuscarProductos(NombreProducto){
    var productos=["Tomate","Lechuga","Berengena","Pimiento"];
        //alert("cliente existe" + NombreCliente)
        //document.getElementById('producto').value = clientes[0];
        
    for (i = 0; i <productos.length; i++) {
      var PrimeraLetraClient=NombreProducto.substring(i,i+1);
      var PrimeraLetraArray=productos[i].substring(i,i+1)
        if (PrimeraLetraClient==PrimeraLetraArray){
            document.getElementById('primer2').value = productos[i];
            return;
        }else{
            alert("no dado de alta");
        }
    
    }
    //document.write(clientes[0]);
 }
 
 function PrecioTotal(cantidad,PrecioUni){
     var precioTo=cantidad*PrecioUni;
     document.getElementById('primer4').value=precioTo;
 }
 
 function TotalCantidad()
 {
     var suma=0;
    for(i=0;i<10;i++){
        //parseInt sirve para convertir algo en entero, para poder sumarlo
        suma=suma+parseInt(document.getElementsByName()("primer"+i).value);
    }
    //vamos a asignar la variable suma 
    document.getElementById("CantidadProducto").value=suma;
     
 }
</script>

<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>Suma de Binarios</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <div id="divContenido"> </div>
       
        
        <! insertamos dos cuadros para introducir los dos numeros en binario >
        <br/>Esta página suma dos números introducidos en binario<br/>
        <br/> Primer nº en binario<br/>
        <input type="text" id="numero1" name="numero1" value="" /> 
        <br/>Segundo nº en binario<br/>
        <input type="text" id="numero2" name="numero2" value="" /><br/>
         <! insertamos un boton, con id y nombre boton, donde muestre
        "Suma", y llame a la función sumarBinario>
     <input type="button" id="boton" name="boton" value="Sumar" onclick="sumaBinario()"/>
        <! insertamos un cuadro para introducir texto que este vacio>
        <input type="text" id="resultado" name="resultado" value="" /> 
    </body>
</html>
<script>
    sumarBinario(){
        var num1="";
        num1=document.getElementById("numero1").value;
        num1=parseInt(num1);
        var num2="";
        num2=document.getElementById("numero2").value;
        num2=parseInt(num2);
        //var resultados=0;
        //resultados=num1 +num2;
        //document.getElementById('resultado').value = resultados;
  
        document.write("la suma es "+(num1+num2));
    }

    
</script>




