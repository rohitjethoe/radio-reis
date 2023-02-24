<template>
    <div ref="main" id="main" lang="nl">
        <Intro v-bind:lang="lang.app.intro" client:load />
        <Player v-bind:lang="lang.app.player" v-bind:data="data"/>
    </div>
</template>

<script>
import langEN from '../languages/en.json';
import langNL from '../languages/nl.json';

import Player from '../components/Player.vue';
import Intro from '../components/Intro.vue';

export default {
    name: "AppComponent",
    data() {
        return {
            currentLang: "nl",
            lang: langNL
        }
    },
    props: {
        data: JSON
    },
    components: {
        Player, Intro
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
        #main {
            width: 800px;
            margin: 0 auto;
        }
    }
</style>