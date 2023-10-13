<script setup>
/* en esta parte va todo el codigo en javascript que necesites
 debido a que solo interpreta en script codigo de javascript*/
const name='vue dinamico'
const name2='color:blue'
const arraycolores=['blue','red'];
const activo=true;
const arrayFrutas=['piña','pedro','ramiro','rosales']
</script>
<template>
  <h1 v-bind:style="name2">azul</h1><!--aqui un detalle importante es no podemos usar los bigotes sino otra forma para la interpolación
  cuando es usarla dentro de las caracteristicas de las etiquetas-->
  <h1>hola {{ name.toUpperCase() }} <!--esto se llama bigotes o interpolación de texto --></h1>
    <h2 v-bind:style="`color:${arraycolores[1]}`">soy rojo</h2>
    <h3>
      {{  activo ?"Estoy Activo":"Estoy Inactivo"}}
    </h3>
    <p v-if="activo==true">Estoy activo</p>
    <p v-else-if="activo==false">Estoy Inactivo</p><!--! con este signo es false si no se cumple la condición se muestra el contenido de la etiqueta-->
    <p v-else>estoy indeciso</p>
    <!--v-if si no necesitas mostrar y ocultar muy seguido pero si usa v-show cuando necesites hacer el proceso varias veces por que no tiene costo de alternacia
    y v-if si necesita costo -->
    <h4 v-show="activo">probando v-show</h4>
      <ul>
        <li v-for="fruta in arrayFrutas">
          {{ fruta }}<!--aqui v-for lo usamos para recorrer el item dentro de los items del arrayFrutas
          fuera de la etiqueta se mostrara el item que se pondra por el largo del recorrido en otras palabras
      el tamño es cuantos items forman parte del array -->
        </li>
      </ul>
</template>
<style>
h1{
  color: aquamarine;
}
</style>