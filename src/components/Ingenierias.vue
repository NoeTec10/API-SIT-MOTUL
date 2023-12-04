
  
<script setup>
import { ref, onMounted } from 'vue';

const info = ref(null);

const fetchData = async () => {
  try {
    const response = await fetch('https://sitmotul.com.mx/api/statusEvalIng');
    info.value = await response.json();

    console.log("Datos de las carreras:", info.value);
  } catch (error) {
    console.log('Error al obtener datos: ', error);
  }
};

onMounted(() => {
  fetchData();
});
</script>

<template>
  <div class="grid grid-cols-1 sm:grid-cols-1 gap-2 place-content-center p-2 sm:p-2 ml-2 ">
    <div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-11/12 sm:w-11/12 md:11/12">
      <div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div class="grid grid-cols-2 sm:grid-cols-2 gap-2 place-content-center p-2 sm:p-2 ">

        <div v-if="info">
          <p class="text-[20px] font-bold">{{ info.ISC.listas !== 0 ? (100 / 244 * info.ISC.listas).toFixed(1) + "%" : 'N/A' }} </p>
        </div>
          <div>
          <p class="text-[8px] font-bold md:mx-4 md:text-xs">Sistemas Computacionales</p>
        </div>

          
      </div>
      
  </div>
  
</div>
<div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-11/12 sm:w-11/12 md:11/12">
      <div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div class="grid grid-cols-2 sm:grid-cols-2 gap-2 place-content-center p-2 sm:p-2 ">

        <div v-if="info">
          <p class="text-[20px] font-bold">{{ info.IEM.listas !== 0 ? (100 / (info.IEM.listas + info.IEM.faltantes)* info.IEM.listas).toFixed(1) + "%" : 'N/A' }} </p>
        </div>
          <div>
          <p class="text-[8px] font-bold md:mx-4 md:text-xs">Electromecánica</p>
        </div>

          
      </div>
      
  </div>
  
</div>
<div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-11/12 sm:w-11/12 md:11/12">
      <div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div class="grid grid-cols-2 sm:grid-cols-2 gap-2 place-content-center p-2 sm:p-2 ">

        <div v-if="info">
          <p class="text-[20px] font-bold">{{ info.IER.listas !== 0 ? ((100 / (info.IER.listas + info.IER.faltantes)) * info.IER.listas).toFixed(1) + "%" : 'N/A' }} </p>
        </div>
          <div>
          <p class="text-[8px] font-bold md:mx-4 md:text-xs">Energias Renovables</p>
        </div>

          
      </div>
      
  </div>
  
</div>
<div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-11/12 sm:w-11/12 md:11/12">
      <div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div class="grid grid-cols-2 sm:grid-cols-2 gap-2 place-content-center p-2 sm:p-2 ">

        <div v-if="info">
          <p class="text-[20px] font-bold">{{ info.IE.listas !== 0 ? ((100 / (info.IE.listas + info.IE.faltantes)) * info.IE.listas).toFixed(1) + "%" : 'N/A' }} </p>
        </div>
          <div>
          <p class="text-[8px] font-bold md:mx-4 md:text-xs">Electronica</p>
        </div>

          
      </div>
      
  </div>
  
</div>
<div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-11/12 sm:w-11/12 md:11/12">
      <div class="rounded-lg bg-indigo-500 h-8 sm:h-8 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div class="grid grid-cols-2 sm:grid-cols-2 gap-2 place-content-center p-2 sm:p-2 ">

        <div v-if="info">
          <p class="text-[20px] font-bold">{{ info.II.listas !== 0 ? ((100 / (info.II.listas + info.II.faltantes)) * info.II.listas).toFixed(1) + "%" : 'N/A' }} </p>
        </div>
          <div>
          <p class="text-[8px] font-bold md:mx-4 md:text-xs">Industrial</p>
        </div>

          
      </div>
      
  </div>
  
</div>

  </div>

</template>





<script>


</script>


