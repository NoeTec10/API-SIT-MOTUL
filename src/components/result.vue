  
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
  
 <div class="ml-4 mr-4 bg-indigo-300">
  <div class="flex items-center justify-center">
  <p class="text-3xl font-bold ms-4">Evaluaciones faltantes y restantes</p>
</div>
  <div class="grid grid-cols-2 sm:grid-cols-5 gap-2 place-content-center sm:p-8 ml-2 ">
    <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 ">
      <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div v-if="info">
          

          <p class="text-1 font-bold">Sistemas Computacionales</p>
        </div>
              <p v-if="info && info.ISC">ISC - Listas: {{ info.ISC.listas }}, Faltantes: {{ info.ISC.faltantes }}</p>
      </div>
  </div>

    <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 transition ease-in-out delay-150 bg-blue-500 hover:-translate-y-1 hover:scale-110 hover:bg-indigo-500 duration-300 ">
      <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div v-if="info">
          
      
          <p class="text-1 font-bold">Electromecánica</p>
        </div>
      <p v-if="info && info.IEM">IEM - Listas: {{ info.IEM.listas }}, Faltantes: {{ info.IEM.faltantes }}</p>
    </div>
  </div>

  <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 transition ease-in-out delay-150 bg-blue-500 hover:-translate-y-1 hover:scale-110 hover:bg-indigo-500 duration-300 ">
      <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div v-if="info">
          <p class="text-1 font-bold">Energias Renovables</p>
        </div>
      <p v-if="info && info.IER">IER - Listas: {{ info.IER.listas }}, Faltantes: {{ info.IER.faltantes }}</p>
    </div>
  </div>

  <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 transition ease-in-out delay-150 bg-blue-500 hover:-translate-y-1 hover:scale-110 hover:bg-indigo-500 duration-300 ">
      <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div v-if="info">
        </div>
        <p class="text-1 font-bold">Electrónica</p>
      <p v-if="info && info.IE">IE - Listas: {{ info.IE.listas }}, Faltantes: {{ info.IE.faltantes }}</p>
    </div>
  </div>

  <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 transition ease-in-out delay-150 bg-blue-500 hover:-translate-y-1 hover:scale-110 hover:bg-indigo-500 duration-300 ">
      <div class="rounded-lg bg-red-500 h-40 sm:h-60 w-32 sm:w-32 flex flex-col items-center justify-center text-center">
        <div v-if="info">
        </div>
        <p class="text-1 font-bold">Industrial</p>
        <p v-if="info && info.II">II - Listas: {{ info.II.listas }}, Faltantes: {{ info.II.faltantes }}</p>
    </div>
  </div>

</div>
</div>







</template>





<script>


</script>