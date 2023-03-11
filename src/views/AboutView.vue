<template>
  <div class="main">
    <div class="productos">
      <div class="Producto">
        <img src="../assets/51QOrzNy7xL._AC_SX450_.jpg" alt="Bocchi" />
        <div>Precio: $ {{ Producto1 }}</div>
        <button @click="Pagar(Producto1)">Agregar</button>
      </div>
      <div class="Producto">
        <img src="../assets/the_weeknd_ok_a1aa13f1 (1).webp" alt="Bocchi" />
        <div>Precio: $ {{ Producto2 }}</div>
        <button @click="Pagar(Producto2)">Agregar</button>
      </div>
      <div class="Producto">
        <img
          src="../assets/73d635_114684fc87794dd1a0e9c64521cbc11e_mv2.webp"
          alt="Bocchi"
        />
        <div>Precio: $ {{ Producto3 }}</div>
        <button @click="Pagar(Producto3)">Agregar</button>
      </div>
      <div class="Producto">
        <img
          src="../assets/below-ghosts-suspended-air-on-260nw-2037732983.webp"
          alt="Bocchi"
        />
        <div>Precio: $ {{ Producto4 }}</div>
        <button @click="Pagar(Producto4)">Agregar</button>
      </div>
    </div>
    <div class="Pagos">
      <div class="cart">El total es ${{ Total }}.</div>
      <PayComponent :cartTotal="Total" />
    </div>
  </div>
</template>

<script>
import PayComponent from "../components/PayComponent.vue";

export default {
  components: {
    PayComponent,
  },
  data() {
    return {
      Producto1: 15590,
      Producto2: 100000.0,
      Producto3: 5000.0,
      Producto4: 20000.0,
      Total: 0,
    };
  },
  methods: {
    Pagar(precio) {
      this.Total += precio;
    },
  },
};
</script>

<style>
.main {
  display: flex;
  height: 80vh;
  width: 100%;
}
.productos {
  display: flex;
  width: 70%;
  justify-content: space-evenly;
  flex-wrap: wrap;
}
.Producto {
  width: 350px;
  height: 45%;
  text-align: center;
  margin-bottom: 20px;
  border: solid 3px rgba(161, 11, 116, 0.534);
}
.Producto img {
  width: 40%;
  margin-top: 10%;
}
.Producto button {
  margin-top: 2%;
}
.Producto div {
  margin-top: 2%;
}
.Pagos {
  margin-left: 10%;
  margin-right: 10%;
}
.cart {
  margin: 15px;
}
</style>
