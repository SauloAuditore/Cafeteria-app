<template>
  <div class="menu bg-white p-6 rounded-lg shadow-lg">
    <h2 class="text-xl font-bold text-gray-800 mb-6">{{ title }}</h2>

    <ul class="space-y-4">
      <li
        v-for="item in menuItems"
        :key="item.id"
        class="flex items-center justify-between border-b pb-3"
      >
        <div class="flex items-center w-full justify-between">
          <p class="text-lg font-semibold text-gray-700 mr-2">{{ item.name }}</p>
          <span class="text-lg font-bold text-gray-800 mr-2">{{ item.price }} €</span>
          <button
            @click="$emit('add-to-cart', item)"
            class="bg-green-500 text-white px-3 py-1 rounded hover:bg-green-600"
          >
            Añadir
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>


<script>
export default {
  props: {
    title: String,
    menuItems: Array,
  },
};
</script>

<style scoped>
/* Estilos generales para el componente de menú */
.menu {
  background-color: #fff;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

/* Estilo de los títulos */
.menu h2 {
  font-size: 1.5rem;
  font-weight: 600;
  color: #4C51BF; /* Color de texto azul */
  margin-bottom: 1.5rem;
}

/* Espaciado entre los items */
.menu li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #e2e8f0;
  padding-bottom: 0.75rem; /* Reducción de espacio en la parte inferior */
  margin-bottom: 0.75rem; /* Reducción de espacio entre los ítems */
}

/* Estilo para el texto de los productos */
.menu .text-lg {
  color: #2d3748; /* Color gris oscuro */
  font-weight: 500;
}

/* Asegura que el nombre, precio y botón estén alineados en una sola fila */
.menu .flex {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.menu .mr-2 {
  margin-right: 0.5rem; /* Reducción de margen entre elementos */
}

/* Estilo para el botón */
button {
  background-color: #48BB78; /* Verde */
  color: white;
  padding: 0.25rem 0.75rem; /* Reducción del padding */
  border-radius: 0.375rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

button:hover {
  background-color: #38A169; /* Verde más oscuro */
}

button:focus {
  outline: none;
  box-shadow: 0 0 0 2px rgba(72, 184, 120, 0.5);
}

button:disabled {
  background-color: #CBD5E0; /* Color gris */
  cursor: not-allowed;
}
</style>
