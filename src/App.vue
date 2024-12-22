<template>
  <div class="container mx-auto p-6">
    <h1 class="text-3xl font-bold mb-6 text-center text-gray-700">Comandas</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
      
      <!-- Menú de Comidas -->
      <MenuComponent
        title="Comidas"
        :menuItems="menuItems.comidas"
        @add-to-cart="addToCart"
      />

      <!-- Menú de Bebidas Calientes -->
      <MenuComponent
        title="Bebidas Calientes"
        :menuItems="menuItems.bebidasCalientes"
        @add-to-cart="addToCart"
      />

      <!-- Menú de Bebidas Frías -->
      <MenuComponent
        title="Bebidas Frías"
        :menuItems="menuItems.bebidasFrias"
        @add-to-cart="addToCart"
      />

      <!-- Carrito de Compras -->
      <CartComponent :cart="cart" @remove-item="removeFromCart" @clear-cart="clearCart" />
    </div>
  </div>
</template>

<script>
import MenuComponent from './components/MenuComponent.vue';
import CartComponent from './components/CartComponent.vue';

export default {
  components: {
    MenuComponent,
    CartComponent,
  },
  data() {
    return {
      menuItems: {
        comidas: [
          { id: 1, name: 'Bizcocho de limón y semillas de amapola', price: 3.5 },
          { id: 2, name: 'Brownie', price: 3.0 },
          { id: 3, name: 'Galletas de chocolate', price: 1.8 },
        ],
        bebidasCalientes: [
          { id: 4, name: 'Latte', price: 2.0 },
          { id: 5, name: 'Capuchino', price: 2.5 },
          { id: 6, name: 'Expresso', price: 1.4 },
          { id: 7, name: 'Chai Latte', price: 2.2 },
        ],
        bebidasFrias: [
          { id: 8, name: 'Iced Late', price: 2.5 },
          { id: 9, name: 'Iced Chai', price: 2.4 },
          { id: 10, name: 'Kombucha', price: 4.0 },
        ],
      },
      cart: [],
    };
  },
  methods: {
    addToCart(item) {
      const cartItem = this.cart.find((i) => i.id === item.id);
      if (cartItem) {
        cartItem.quantity++;
      } else {
        this.cart.push({ ...item, quantity: 1 });
      }
    },
    removeFromCart(index) {
      this.cart.splice(index, 1);
    },
    clearCart() {
      this.cart = [];
    },
  },
};
</script>

<style scoped>
/* Fondo general de la página */
body {
  background-color: #f7fafc; /* Fondo gris claro */
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

/* Contenedor principal */
.container {
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

/* Estilo para el encabezado */
h1 {
  color: #4C51BF; /* Color de texto azul violeta */
  text-align: center;
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 2rem;
}

/* Estilo para los grid */
.grid {
  gap: 2rem;
}
</style>

