<template>
    <div class="text-6xl">
        <div class="mt-32">
            <div class="font-word">
                <div v-if="!switchSummands">
                    {{ summandA }} + {{ summandB }}
                </div>
                <div v-else>
                    {{ summandB }} + {{ summandA }}
                </div>
            </div>
        </div>
    </div>

</template>
<script>
    export default {
        name: 'Addition',
        props: {
            level: { type: Number, required: true },
        },
        data () {
            return {
                summandA: 0,
                summandB: 0,
                switchSummands: false,
            };
        },
        computed: {
            sumMin () {
                switch (this.level) {
                    case 1:
                        return 3;
                    case 2:
                        return 8;
                    case 3:
                        return 12;
                    case 4:
                        return 16;
                    case 5:
                        return 25;
                    default:
                        return 3;
                }
            },
            sumMax () {
                switch (this.level) {
                    case 1:
                        return 8;
                    case 2:
                        return 12;
                    case 3:
                        return 16;
                    case 4:
                        return 25;
                    case 5:
                        return 40;
                    default:
                        return 8;
                }
            },
        },
        created () {
            this.generateSummands();
        },
        methods: {
            generateSummands () {
                const sum = Math.floor(Math.random() * (this.sumMax - this.sumMin)) + this.sumMin;
                this.summandA = Math.floor(Math.random() * sum);
                this.summandB = sum - this.summandA;
            },
            prev () {
                this.generateSummands();
            },
            next () {
                this.generateSummands();
            },
            toggle () {
                this.switchSummands = !this.switchSummands;
            },
        },
    };
</script>
