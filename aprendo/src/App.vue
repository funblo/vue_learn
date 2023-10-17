<script setup>
/* en esta parte va todo el codigo en javascript que necesites
 debido a que solo interpreta en script codigo de javascript*/
const name1='vue dinamico'
const name2='color:blue'
const arraycolores=['blue','red'];
const activo=true;
const arrayFrutas2 = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];
const objeto1={
  name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
} 

    const arrayFrutas = [
        {
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
        },
        {
            name: "Pera",
            price: "$2.00",
            description: "Una pera",
        },
        {
            name: "Naranja",
            price: "$3.00",
            description: "Una naranja",
        },
    ];
const arrayFrutas1=['piña','pedro','ramiro','rosales']
</script>
<template>
  <ul>
    <template v-for="fruta in arrayFrutas2" :key=fruta.name >
      <li v-if="fruta.stock>0">
        name: {{ fruta.name}} <br> price: {{ fruta.price }} <br> description: {{ fruta.description }} <br> stock: {{ fruta.stock }}
      </li>
    </template>
  </ul>
  <!--Cuando existen en el mismo nodo, v-if tiene una prioridad más alta que v-for, ten cuidado con los 
  arreglos porque si lo pones siempre leera primero v-if antes que el arreglo y por eso no dara respuesta.
  por eso es importante la siguiente solución usamos la etiqueta template para usar for y lea el arreglo 
  primero y despues lea con otra etiqueta el if-->
  <h4>Propiedades</h4>
  <ul>
    <li v-for="(value,propiedades,index) in objeto1"
    :key="value"    
    >
    {{ index }}- {{ propiedades }}: {{ value}}<!--aqui recorre cada una de sus propiedades del objeto-->
    </li>
  </ul>
  <h4>Arreglo frutas</h4>
  <ul>
    <li v-for="frutas in arrayFrutas" :key="frutas.name">
      {{ frutas.name }}_{{ frutas.price }}<!--esto es mandar a llamar una caracteristica de un objeto dentro del array-->

    </li>
  </ul>
  <h1 v-bind:style="name2">azul</h1><!--aqui un detalle importante es no podemos usar los bigotes sino otra forma para la interpolación
  cuando es usarla dentro de las caracteristicas de las etiquetas-->
  <h1>hola {{ name1.toUpperCase() }} <!--esto se llama bigotes o interpolación de texto --></h1>
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
        <li v-for="fruta in arrayFrutas1">
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