
  
  <script setup>
  import { ref, onMounted, computed } from 'vue';
  import dayjs from 'dayjs';
import Ingenierias from './Ingenierias.vue';
import result from './result.vue';

  const info = ref({
    periodo: "",
    alTotal: "",
    alEvaluados: "",
    inicio: "",
    fin: "",
  });

  const formatoFechaInicio = computed(() => {
  // Asume que info.inicio contiene la fecha en formato ISO
  return dayjs(info.value.inicio).format('DD-MM-YYYY');
});

const formatoFechaFin = computed(()=>{
    return dayjs(info.value.fin).format('DD-MM-YYYY')
})

const diferenciaHoras = computed(()=>{
  const now = dayjs();
  const finDia = dayjs(info.value.fin);
  
  // Obtener la diferencia en horas
  const diferenciaHora = finDia.diff(now, 'hour');

  return diferenciaHora;
})
  
  const fetchData = async () => {
    try {
      const response = await fetch('https://sitmotul.com.mx/api/statusEval');
      const data = await response.json();
      info.value = data;
    } catch (error) {
      console.log('Error al obtener datos: ', error);
    }
  };
  
  onMounted(() => {
    fetchData();
  });
  
  </script>
  

  <template>

<nav class="bg-yellow-600 italic font-serif w-full text-white flex flex-col md:flex-row md:justify-between md:px-2 md:py-2 text-xl">
        <div class="flex justify-center md:gap-4">
          <img src="./logo.svg" class="w-10 h-10 " alt="logo">
            
        </div>
        <div class="flex flex-col md:flex-row text-center md:gap-5">
            <ul class="py-1">
              <p class="text-lg font-bold">SIT Motul</p>
            </ul>
        </div>
    </nav>
        
           <div class=" flex justify-center md:gap-4 ">
               
            </div>
           

            <div class="bg-indigo-300">
  <div class="grid grid-cols-2 sm:grid-cols-2 gap-2 place-content-center sm:p-2 ">
    <div class="rounded-lg bg-indigo-500 h-72 sm:h-60 w-auto sm:w-auto ">
      <p class="text-xs font-bold mx-8" v-if="info && info.periodo"> Estado de la evaluación del tutor Periodo: {{  info.periodo }}</p>
         
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 place-content-center sm:p-2 ">

            <div class="p-2  bg-red-400 rounded-br rounded-lg p-2"><p class="text-xs font-bold rounded-tl rounded-br md:rounded-none w-full md:w-11/12 md:ml-2 md:rounded-br md:rounded-lg" v-if="info && info.alTotal">Total de alumnos: {{ info.alTotal + " alumnos" }}</p></div>
            <div class="p-2  bg-green-600 rounded-br rounded-lg p-2"><p class="text-xs font-bold rounded-tl rounded-br md:rounded-none w-full md:w-11/12 md:ml-2 md:rounded-br md:rounded-lg " v-if="info && info.alEvaluados">Alumnos evaluados: {{ info.alEvaluados }}</p></div>
            
            </div>
            <div class="grid grid-cols-2 sm:grid-cols-2 gap-2 place-content-center sm:p-2">
              <div class="p-2 bg-green-400 rounded-br rounded-lg p-2"><p  class="text-xs font-bold rounded-tl rounded-br md:rounded-none w-full md:w-11/12 md:ml-2 md:rounded-br md:rounded-lg" v-if="info && info.inicio">Inicio: {{ formatoFechaInicio }}</p></div>
              <div class="p-2 bg-rose-300 rounded-br rounded-lg p-2"><p  class="text-xs font-bold rounded-tl rounded-br md:rounded-none w-full md:w-11/12 md:ml-2 md:rounded-br md:rounded-lg" v-if="info && info.fin">Fin: {{ formatoFechaFin }}</p></div>
          </div>
          <div class="flex items-center justify-center py-8">
<div class="flex flex-col-reverse  bg-amber-200 p-2 rounded-tl rounded-br rounded-lg">
    <p  class="text-xs font-bold rounded-tl rounded-br md:rounded-none w-full md:w-11/12 md:ml-2 md:rounded-br md:rounded-lg" v-if="info && info.fin">Tiempo por concluir {{ diferenciaHoras + "h"}}</p>
  </div>
</div>
      </div> 
      

        <div class="rounded-lg bg-green-500 h-40 sm:h-60 w-auto sm:w-auto ">
      <p class="text-sm font-bold ms-8">Estado de la evaluación por ingeniería</p>    
      <Ingenierias></Ingenierias>
      </div>

     
  </div>
  <result></result>
</div>
  </template>