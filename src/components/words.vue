<template>
    <div :class="fontSize">
        <div class="mt-32">
            <span class="font-word" :class="{uppercase: uppercase}">{{ word }}</span>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'Words',
        data () {
            return {
                words: [
                    'Hase',
                    'Boot',
                    'Hose',
                    'Baum',
                    'Haus',
                    'Maus',
                    'Rose',
                    'Wal',
                    'Puppe',
                    'Suppe',
                    'Sand',
                    'Wand',
                    'Nase',
                    'Mund',
                    'Haare',
                    'Wind',
                    'Blatt',
                ],
                wordIndex: 0,
                uppercase: true,
                skipWords: 1,
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
        created () {
            this.skipWords = Math.floor(Math.random() * this.words.length);
        },
        methods: {
            prev () {
                this.wordIndex = (this.wordIndex - this.skipWords + this.words.length) % this.words.length;
            },
            next () {
                this.wordIndex = (this.wordIndex + this.skipWords) % this.words.length;
            },
            toggle () {
                this.uppercase = !this.uppercase;
            },
        },
    };
</script>
