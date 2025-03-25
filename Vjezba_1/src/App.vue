<script setup>

import { ref } from 'vue'


</script>


<template>
    <div ref="dark" class="">
        <div @click="$refs.dark.classList.toggle('dark');" 
        class=" bg-gradient-to-br from-red-800 to-green-500 dark:from-emerald-950 dark:to-indigo-950
        min-h-screen">

            <div class="text-6xl text-teal-100 text-center">
                Pozdrav, ja sam <span class="text-cyan-400 font-bold">Mateo Šegon</span>
            </div>
            <hr class="w-[1024px] border-2 opacity-75 rounded-sm mx-auto my-5 border-teal-100" />


        <div class="text-2xl text-teal-100/75 mx-auto pl-3 my-5 max-w-[1024px]">Moji omiljeni filmovi:</div>
                <div class="flex gap-2 items-center justify-center ">
                    <div class="flex flex-col items-center">
                        <img src="https://resizing.flixster.com/-XZAfHZM39UwaGJIFWKAE8fS0ak=/v3/t/assets/p10543523_p_v8_as.jpg" class="w-[320px] h-[480px] rounded-md">
                        <span class="text-2xl py-5 text-teal-100">Interstellar</span>
                    </div>
                    <div class="flex flex-col items-center">
                        <img src="https://resizing.flixster.com/fC7nU6iTRQk02tS0SDS1ylx-G34=/ems.cHJkLWVtcy1hc3NldHMvbW92aWVzL2QxZjE5ZDgzLTRiY2MtNDFkYS04NWQ4LTRkYzc1ZTAwNWE2NC53ZWJw" class="w-[320px] h-[480px] rounded-md">
                        <span class="text-2xl py-5 text-teal-100">Endgame</span>
                    </div>
                    <div class="flex flex-col items-center">
                        <img src="https://m.media-amazon.com/images/M/MV5BNzVkMTgzODQtMWIwZC00NzE4LTgzZjYtMzAwM2I5OGZhNjE4XkEyXkFqcGc@._V1_FMjpg_UX1000_.jpg" class="w-[320px] h-[480px] rounded-md">
                        <span class="text-2xl py-5 text-teal-100">Ready player one</span>
                    </div>
                </div>
        </div>
    </div>

</template>

