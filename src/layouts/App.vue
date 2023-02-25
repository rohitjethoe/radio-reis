<template>
    <div ref="main" id="main" lang="nl">
        <Intro v-bind:lang="lang.app.intro" client:load />
        <Player v-bind:lang="lang.app.player" v-bind:currentRadio="currentRadio" v-bind:data="data"/>
        <Select @changeRadio="changeRadio" v-bind:lang="lang.app.select" v-bind:data="data.radios"/>
    </div>
</template>

<script>
import langEN from '../languages/en.json';
import langNL from '../languages/nl.json';

import Intro from '../components/Intro.vue';
import Player from '../components/Player.vue';
import Select from '../components/Select.vue';

export default {
    name: "AppComponent",
    data() {
        return {
            currentLang: "nl",
            lang: langNL,
            currentRadio: this.data.radios.nl[2]
        }
    },
    props: {
        data: JSON
    },
    components: {
        Player, Intro, Select
    },
    methods: {
        changeRadio: function (value) {
            this.currentRadio = this.data.radios[value.country][value.id];
        }
    },
    created() {
        setInterval(() => {
            if (this.$refs.main !== undefined) {
                this.currentLang = this.$refs.main.attributes.lang.value;
                this.currentLang == "nl" ? this.lang = langNL : this.lang = langEN;
            }
        }, 1000);
    }
}
</script>

<style lang="scss">
    @media only screen and (min-width: 800px) {
        // #main {
        //     width: 800px;
        //     margin: 0 auto;
        // }
    }
</style>