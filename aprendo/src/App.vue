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
//metodo sin parametros o sin argumentos
const click =()=>{
  console.log('hola')
}
const click1=(message)=>{
  console.log(message)
}
//aprendizaje profundo
import {computed, ref} from 'vue';
const arraynumeros =ref([])/*aqui el array agrega numeros favoritos, por lo que tal array es reactivo al solicitar que se
cambie la cantidad que contiene el arreglo asi como su contenido debido a que html solo muestra puedes agregar logica pero
dificulta la lectura de componenetes*/
const add=() => {
  arraynumeros.value.push(counter1.value)// al hacer push mi numero o mi valor es cargado al arreglo.
} 
const stopadd=computed(() => {
//al hacer un computado puedo usar logica condicional para devolver valores que cumplan o incumplan la condición
   const serachnum=arraynumeros.value.find((num)=>num==counter1.value)
/*se le da el valor del numero que se repite a search y con find es buscar un valor EN ESTE CASO DENTRO DEL ARREGLO primero se declara
la variable o const para moverse entre los valores contenidos en el arreglo y al final aplicamos la condicional en donde comparamos si existe
el numero del contador dentro del arreglo*/
    if(serachnum===0)return true//se hace esto debido a que en valor booleano 0 es false por lo que la maquina entiende que la repeticón no se cumplió
    return serachnum ? true :false //Si ocurre la repeticion de un numero en especifico sera true en caso contrario false
})
let counter=0
let counter1= ref(0);//es una variable reactiva
const increment=()=>{
  console.log('Aumentar contador')
  counter++
}
const increment2=()=>{
  console.log('Aumenta')
  counter1.value++//aqui esta escrito como objeto el counter1 por eso se habla de su valor contenido
}

const increment1=()=>{
  console.log('Disminuye')
  counter1.value--
}
const increment3=()=>{
  console.log('se reseteo')
  counter1.value=0
}
const color=computed (()=>{
  if(counter1.value<0 ){
    return 'negative'
  }
  if(counter1.value===0){
    return 'zero'
  }
  if(counter1.value>0){
    return 'positive'
  }
})
</script>
<template>
  <ul>
    <template v-for="fruta in arrayFrutas2" :key=fruta.name >
      <li v-if="fruta.stock>0" >
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
      <button @click="click">Activame</button>
      <button v-on:click="click1('texto 1')">Guardar</button>
      <button @click="click1('texto 2')">activame1</button>
      <!--esto lo que sigue son modificadores-->
      <button @click.right="click1('se pico el right')">right</button>
      <button @click.left="click1('se pico left en mouse')">left</button>
      <button @click.middle="click1('middle')">middle</button>
      <button @click="increment">Aumentar contador</button>
      <button @click="increment1">Disminuir Contador</button>
      <button @click="increment2"> Aumentar Contador</button>
      <button @click="increment3">Reseatear Contador</button>
      <button :disabled="true">add</button>
      <h4>{{ counter }}</h4><!--es importante la reactividad para generar un nuevo renderizado en ek h4 y no se quede estatico
      con el numero de el principio-->
      <h4 :class="counter1>0 ? 'positive':'negative'">{{ counter1 }}</h4><!--clases dinamicas como con el if ?-->
        <h4 :class="color">{{ counter1 }}</h4><!--mejor forma para que el proceso sea para la logica y no el mismo navegador, dificulta 
        interpretación de nuestros componentes-->
      
      <br>
      <br>
      <div class="cointainer text-center">
      <h2>-----------Practica --------------------------</h2>

      <button @click="increment1" class="btn btn-primary">Disminuir Contador</button>
      <button @click="increment2" class="btn btn-success"> Aumentar Contador</button>
      <button @click="increment3" class="btn btn-danger">Reseatear Contador</button>
      <button @click="add" :disabled="stopadd" class="btn btn-secondary">add</button>
      <h4 :class="color">{{ counter1 }}</h4>
      </div>
      
</template>
<style>
.positive{
  color: green;
}
.negative{
  color: red;
}
.zero{
  color: black;
}
h1{
  color: aquamarine;
}
</style>