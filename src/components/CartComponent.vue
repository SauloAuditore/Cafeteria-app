<template>
    <div class="cart">
      <h2 class="text-xl font-bold mb-4">Carrito</h2>
      <ul>
        <li
          v-for="(item, index) in cart"
          :key="index"
          class="flex justify-between items-center mb-2"
        >
          <span>{{ item.name }} x {{ item.quantity }} - {{ item.price * item.quantity }} €</span>
          <button
            @click="$emit('remove-item', index)"
            class="bg-red-500 text-white px-2 py-1 rounded hover:bg-red-600"
          >
            Eliminar
          </button>
        </li>
      </ul>
      <p class="font-bold">Total: {{ totalPrice }} €</p>
      <button
        @click="$emit('clear-cart')"
        class="bg-gray-500 text-white px-3 py-1 rounded hover:bg-gray-600 mt-4"
      >
        Vaciar Carrito
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['cart'],
    computed: {
      totalPrice() {
        return this.cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
      },
    },
  };
  </script>
  
  <style scoped>
/* Estilos generales para el componente de carrito */
.cart {
  background-color: #fff;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

/* Estilo de los títulos */
.cart h2 {
  font-size: 1.5rem;
  font-weight: 600;
  color: #4C51BF; /* Color de texto azul */
  margin-bottom: 1.5rem;
}

/* Espaciado entre los items del carrito */
.cart li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #e2e8f0;
  padding-bottom: 1rem;
  margin-bottom: 1rem;
}

/* Estilo para los precios */
.cart .font-semibold {
  color: #2d3748; /* Color gris oscuro */
  font-weight: 700;
}

/* Estilo del precio total */
.cart p {
  font-size: 1.25rem;
  font-weight: 700;
  color: #4C51BF; /* Color azul */
}

/* Estilos para el botón de eliminar */
button {
  background-color: #F56565; /* Rojo */
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 0.375rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

button:hover {
  background-color: #E53E3E; /* Rojo más oscuro */
}

button:focus {
  outline: none;
  box-shadow: 0 0 0 2px rgba(245, 101, 101, 0.5);
}

/* Estilos para el botón de vaciar carrito */
button.clear-cart {
  background-color: #A0AEC0; /* Gris */
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 0.375rem;
  width: 100%;
}

button.clear-cart:hover {
  background-color: #718096; /* Gris más oscuro */
}

button.clear-cart:focus {
  outline: none;
  box-shadow: 0 0 0 2px rgba(160, 174, 192, 0.5);
}
</style>
