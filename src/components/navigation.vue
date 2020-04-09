<template>
    <div class="flex">
        <div class="w-1/3 p-2"><div @click="$emit('prev')" class="rounded-full bg-red-500 p-4 text-center text-white">prev</div></div>
        <div class="w-1/3 p-2"><div @click="$emit('configuration')" class="rounded-full bg-red-200 p-4 text-center">config</div></div>
        <div class="w-1/3 p-2"><div @click="$emit('next')" class="rounded-full bg-red-500 p-4 text-center text-white">next</div></div>
    </div>
</template>
<script>
    export default {
        name: 'Navigation',
    };
</script>
