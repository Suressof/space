<script setup>
// import HelloWorld from './components/HelloWorld.vue';

// import HelloWorld from './components/HelloWorld.vue'
//     import {ref} from 'vue';
//     const count = ref(0);
//     const inc = ()=>count.value++;

//  import {ref} from 'vue'
//  const count = ref(0);


//  function inc() {
//   count.value++
//   console.log(count)
//  }

  // function  upd(event) {
  //     count.value = Number(event.target.value)
  // }

</script> 

<template>
  <header class="flex justify-between border-b px-8 py-8" style="background: radial-gradient(circle at top left, #2b1055, #200722, #090a1a);
">
    <div class="flex items-center" >
      <img src="/src/assets/в32ац.png" width="150px" >
      <div class="p-3">
        <h1 style="font-size: xx-large; color: whitesmoke; text-shadow: #090a1a 10px 5px;"><b>Space Engine</b></h1>
        <p style="width: 50%; color: grey;">Тёмная материя и энергия: самые загадочные элементы вселенной</p>

      </div>
    </div>
      <ul class="flex items-center gap-10">
        <li class="flex items-center gap-3">
          <img src="/src/assets/defwf.svg" width="30"><span style="color: aliceblue;">1200 руб.</span>
        </li>
        <li class="flex items-center gap-3">
          <img src="/src/assets/heart.svg" width="20"><span style="color: aliceblue;">Загладки</span>
        </li>
      </ul>
  
    <!-- <div class="mt-20">
      <HelloWorld title="Puma" :price="9500 + 1000" isAdded="true"/>
    </div>
    <div class="mb-40">
      <HelloWorld title="Puma" :price="9500 + 1000" isAdded="true"/>
    </div> -->
  </header>

</template>


