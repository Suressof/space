<script setup>
import Header from './components/header.vue'
import { ref, reactive, computed, onMounted } from 'vue';
import axios from 'axios';

// Загружаемые элементы
const items = ref([]);

// Фильтры (поиск и сортировка)
const filters = reactive({
  sortBy: '',
  searchQuery: '',
});

// Получение данных с сервера
const fetchItems = async () => {
  try {
    const response = await axios.get('https://3ddb694c8e586df5.mokky.dev/items');
    if (response.data && Array.isArray(response.data)) {
      items.value = response.data;
    } else {
      console.error('Некорректные данные от сервера:', response.data);
    }
  } catch (error) {
    console.error('Ошибка при загрузке данных:', error);
  }
};

// Сортировка и поиск
const sortedAndFilteredItems = computed(() => {
  let result = [...items.value];

  // Сортировка
  if (filters.sortBy === 'price') {
    result.sort((a, b) => a.price - b.price);
  } else if (filters.sortBy === '-price') {
    result.sort((a, b) => b.price - a.price);
  } else if (filters.sortBy === 'name') {
    result.sort((a, b) => a.name.localeCompare(b.name));
  }

  // Поиск
  if (filters.searchQuery) {
    result = result.filter(item =>
      item.name.toLowerCase().includes(filters.searchQuery.toLowerCase())
    );
  }

  return result;
});

// Инициализация данных
onMounted(() => {
  fetchItems();
});
</script>

<template>
  <Header/>
  <div class="container mx-auto p-4">
    <!-- Фильтры -->
    <div class="flex justify-between items-center mb-4">
      <!-- Сортировка -->
      <select
        v-model="filters.sortBy"
        class="border rounded-md py-2 px-3"
      >
        <option value="" disabled>Сортировать по</option>
        <option value="name">По названию</option>
        <option value="price">По цене (дешевые)</option>
        <option value="-price">По цене (дорогие)</option>
      </select>

      <!-- Поиск -->
      <input
        v-model="filters.searchQuery"
        type="text"
        placeholder="Поиск..."
        class="border rounded-md py-2 px-3"
      />
    </div>

    <!-- Список товаров -->
    <div v-if="sortedAndFilteredItems.length" class="grid grid-cols-1 md:grid-cols-3 gap-4">
      <div
        v-for="item in sortedAndFilteredItems"
        :key="item.id"
        class="border rounded-lg p-4 shadow-md"
      >
        <img :src="item.image" alt="Товар" class="w-full h-48 object-cover mb-2" />
        <h3 class="text-lg font-bold">{{ item.name }}</h3>
        <p class="text-gray-500">{{ item.price }} $.</p>
      </div>
    </div>

    <!-- Сообщение об отсутствии данных -->
    <div v-else class="text-center text-gray-500">
      <p>Нет товаров для отображения.</p>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 800px;
}
</style>
