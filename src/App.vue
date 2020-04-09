<template>
    <div id="app" class="flex flex-col min-h-screen">
        <header class="m-2">
            <navigation @prev="prev" @next="next" @configuration="configurationModalActive = true"/>
        </header>
        <main class="flex-grow text-center">
            <component
                    :is="currentComponent"
                    :level="level"
                    ref="component"
            />
        </main>
        <footer class="m-2">
            <div class="flex justify-center">
                <div @click="toggle" class="w-2/3 bg-blue-500 text-center rounded-full p-8">a/A</div>
            </div>
        </footer>
        <modal
                title="Übungen"
                :active="configurationModalActive"
                @close="configurationModalActive = false"
        >
            <ul>
                <li class="mt-2" @click="loadComponent('Words')">Lesen</li>
                <li class="mt-8" @click="loadComponent('Addition', 1)">Rechnen 1</li>
                <li class="mt-2" @click="loadComponent('Addition', 2)">Rechnen 2</li>
                <li class="mt-2" @click="loadComponent('Addition', 3)">Rechnen 3</li>
                <li class="mt-2" @click="loadComponent('Addition', 4)">Rechnen 4</li>
                <li class="mt-2" @click="loadComponent('Addition', 5)">Rechnen 5</li>
            </ul>
        </modal>
    </div>
</template>

<script>
    import Addition from './components/addition';
    import Navigation from './components/navigation';
    import Modal from './components/modal';
    import Words from './components/words';

    export default {
        name: 'app',
        components: {
            Addition,
            Navigation,
            Modal,
            Words,
        },
        data () {
            return {
                currentComponent: Words,
                configurationModalActive: false,
                level: 1,
            };
        },
        methods: {
            prev () {
                this.$refs.component.prev();
            },
            next () {
                this.$refs.component.next();
            },
            toggle () {
                this.$refs.component.toggle();
            },
            loadComponent (component, level) {
                this.currentComponent = component;
                this.level = level;
                this.configurationModalActive = false;
            },
        },
    };
</script>

<style>
</style>
