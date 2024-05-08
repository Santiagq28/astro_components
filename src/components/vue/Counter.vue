<script setup>
    import { ref } from 'vue';

    let number = ref(0);
    let time = ref(0);
    let interval;

    function add(){
        if (number.value ==0){
            interval = setInterval(() => {
                time.value++
            }, 1000)
        }
        number.value++;
        
        if (number.value == 100){
            clearInterval(interval);
        }
        }
</script>

<template>
    <div v-show="number > 0" class="float-right mr-8 bg-red-200 rounded inline-block py-1 px-2">
        Tiempo: {{ time }}
    </div>
    <div @click="add" class="hover:cursor-pointer select-none bg-green-600 text-white py-1 px-2 rounded w-12 text-center mt-10 m-auto">
        {{ number }}
    </div>
    <div v-if="number == 0" class="bg-orange-300 rounded py-1 px-2 w-52 mt-8 mx-auto text-center">
        ¿Clickear? ¡o miedo! 👀
    </div>
    <div v-else-if="number < 50 && time >9" class="bg-red-500 rounded py-1 px-2 w-52 mt-8 mx-auto text-center">
        ¿No tienes manos o que? 🥱
    </div>
    <div v-else-if="number == 100 && time <10" class="bg-red-500 rounded py-1 px-2 w-52 mt-8 mx-auto text-center">
        Wow, más lento vaquero 😎
    </div>
    <div v-else  class="bg-green-500 rounded py-1 px-2 w-52 mt-8 mx-auto text-center">
        GO! GO! GO! 🐔
    </div>
</template>