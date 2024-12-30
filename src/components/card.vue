<script setup>

defineProps ({
    name: String,
    image: String,
    price: Number,
    isFavorite: Boolean,
    isAdded: Boolean,
    onClickAdd: Function,
    onClickFavorite: Function
});


</script>
<template>
<div style="display: flex; flex-wrap: wrap; margin-top: 10px; justify-content: center; gap: 10px" class="relative transition hover:-translate-y-2 hover:shadow-xl">
    
      <img :src="!isFavorite ? '/src/assets/like-1.svg' : '/src/assets/like-2.svg'" @click="onClickFavorite" style="position: absolute; top: 0; left: 0;">
      <img :src="image" width="200px" >
      <p class="mt-2"><i>{{ name }}</i></p>
      <!-- <img src="/src/assets/heart.svg" class="top-left-image"> -->
      <div class="flex m-5  mt-5">
        <div class="flex flex-col">
            <span class="text-slate-400">Цена: </span>
            <b>{{price}} $</b>
        
          <img :src="isAdded ? '/src/assets/plus.svg' : '/src/assets/checked.svg'" alt="Plus" > 
        </div>
        </div>
    </div>
    
</template>

<script>
// export default {
//   methods: {
//     changeToRed() {
//       const imgElement = this.$refs.imgElement;
//       if (imgElement) {
//         imgElement.src = '/src/assets/plus-red.svg'; // Меняем изображение на красное
//       } else {
//         console.error('Элемент img не найден');
//       }
//     },
//     changeToDefault() {
//       const imgElement = this.$refs.imgElement;
//       if (imgElement) {
//         imgElement.src = '/src/assets/plus.svg'; // Возвращаем исходное изображение
//       } else {
//         console.error('Элемент img не найден');
//       }
//     }
//   }
// };
</script>

<style scoped>
.container {
  position: relative;
  width: 200px; /* Ширина контейнера */
  height: 300px; /* Высота контейнера */
}

.background-image {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Масштабирует фон */
}

.top-left-image {
  position: absolute;
  top: 0; /* Верхний край */
  left: 0; /* Левый край */
  margin: 10px;
  width: 30px; /* Ширина картинки сверху */
  height: auto; /* Сохраняет пропорции */
  z-index: 10; /* Размещает изображение поверх фона */
  cursor: pointer;
}
.top-left-image:hover {
  content: url('/src/assets/fasffa.png'); /* Смена через URL */
}
</style>