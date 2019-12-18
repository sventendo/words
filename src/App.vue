<template>
    <div id="app" class="flex flex-col min-h-screen">
        <header class="m-2">
            <navigation @prev="prevWord" @next="nextWord" @configuration="toggleConfiguration"/>
        </header>
        <main class="flex-grow text-center" :class="fontSize">
            <div class="mt-32">
                <span class="font-word" :class="{uppercase: uppercase}">{{ word }}</span>
            </div>
        </main>
        <footer class="m-2">
            <div class="flex justify-center">
                <div @click="uppercase = !uppercase" class="w-2/3 bg-blue-500 text-center rounded-full p-8">a/A</div>
            </div>
        </footer>
    </div>
</template>

<script>
    import Navigation from './components/Navigation';

    export default {
        name: 'app',
        components: {
            Navigation,
        },
        data () {
            return {
                words: [
                    'Hallo',
                    'Alma',
                ],
                wordIndex: 0,
                uppercase: true,
            };
        },
        computed: {
            word () {
                return this.words[ this.wordIndex ];
            },
            fontSize () {
                if (this.word.length < 8) {
                    return 'text-6xl';
                } else if (this.word.length < 10) {
                    return 'text-5xl';
                } else if (this.word.length < 12) {
                    return 'text-4xl';
                } else if (this.word.length < 15) {
                    return 'text-3xl';
                } else if (this.word.length < 20) {
                    return 'text-2xl';
                } else {
                    return 'text-xl';
                }
            },
        },
        methods: {
            prevWord () {
                this.wordIndex = (this.wordIndex - 1 + this.words.length) % this.words.length;
            },
            nextWord () {
                this.wordIndex = (this.wordIndex + 1) % this.words.length;
            },
            toggleConfiguration () {

            },
        },
    };
</script>

<style>
</style>
