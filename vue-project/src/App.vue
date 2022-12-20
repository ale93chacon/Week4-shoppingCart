<script>
import { computed } from "@vue/reactivity";
import ITEMS from "./assets/items.json";
export default{
  data(){
    return{
      items: ITEMS,


    }
  },
  computed: {
    chooseItems(){
//alert(this.quantity[0])
console.log("hoooooolaaaa" + this.items[0].quantity);
console.log("adiooooos" + this.items.length)
      return this.items.slice(0,5);
    },
  calculateTotalItems(){
    let contador= 0;
    for(let i=0; i<this.items.length; ++i){
      console.log("resultadooooo" + i + " " + contador);
     contador+= this.items[i].quantity;
    }
    return contador;
    console.log("contadoooooor" + contador);
  },
  calculateSubtotal(){
    let counter= 0;
  
    for(let i=0; i<this.items.length; ++i){
    
     counter+= this.items[i].quantity * this.items[i].price;
    }
    return counter;
    console.log("contadoooooor" + counter);
    }
  }
  }

</script>

<template>
<nav>
  <header>
    <h1 class="text-2xl text-green-800 ">My supper ecommerce</h1>
  </header>

</nav>
<section>
  <table>
    <thead>
    <tr>
    <th>name</th>
    <th>photo</th>
    <th>price</th>
    <th>quantity</th>
    <th>Total</th>
    </tr>
  </thead>
  <tbody v-for="valor of chooseItems" :key="valor.uuid">

    <tr>
      <td>{{valor.name}}</td>
      <td><img class="w-48" :src="valor.image" :alt="valor.name"></td>
      <td>{{valor.price}}</td>
      <td><input type="number" v-model="valor.quantity" ></td>
      <td>{{valor.price * valor.quantity}} </td>
    </tr>
    
  </tbody>
  
  </table>
<br>
<div>CARRITO: {{calculateTotalItems}} artículos</div>

<br>
<div>SUBTOTAL IS: {{calculateSubtotal}}</div>
</section>

<footer>
  <ul>
    <li>productos</li>
    <li>Servicios</li>
    <li>Contacto</li>
  </ul>
</footer>
</template>

<style scoped>


</style>
