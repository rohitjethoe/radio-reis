<template>
  <div>
    <audio ref="player" crossorigin="anonymous" autoplay>
        <source v-bind:src="currentRadio.url" type="audio/ogg">
        <source v-bind:src="currentRadio.url" type="audio/mpeg">
    </audio>
    <div class="player">
        <div class="heading">
            <div class="title">
                <h3>{{ lang.title }}</h3>
            </div>
            <div class="date">
                {{ date.getDate() }} {{ lang.dates.months[date.getMonth()] }}
            </div>
        </div>
        <div class="audio-wave">
            <pre v-bind:class="playing ? '' : 'wave-inactive'" class="wave wave-1">{{ data.playing[0][0] }}</pre> <br>
            <pre v-bind:class="playing ? '' : 'wave-inactive'" class="wave wave-2">{{ data.playing[1][0] }}</pre> <br>
            <pre v-bind:class="playing ? '' : 'wave-inactive'" class="wave wave-3">{{ data.playing[2][0] }}</pre> <br>
            <pre v-bind:class="playing ? '' : ''" class="wave wave-3">---------------------</pre>
        </div>
        <div class="controls">
            <div @click="$event => playingController()" class="control-item play">
                <i v-if="playing" class="fa-solid fa-pause"></i>
                <i v-else class="fa-solid fa-play"></i>
            </div>
            <div class="control-item name">{{ currentRadio.name }}</div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name: "PlayerComponent",
    data() {
        return {
            playing: true,
            date: new Date(),
        }
    },
    props: {
        data: JSON, lang: JSON, currentRadio: JSON
    },
    methods: {
        playingController: function() {
            const audio = document.querySelector('audio');
            this.playing = !this.playing;
            this.playing ? audio.play() : audio.pause();
        },
        startWaveform: function() {
            let x = 0;
            setInterval(() => {
                const wave = document.querySelectorAll('.wave');
                if (x < 5) {
                    wave[0].innerHTML = this.data.playing[0][x];
                    wave[1].innerHTML = this.data.playing[1][x];
                    wave[2].innerHTML = this.data.playing[2][x];
                    x++;
                } else {
                    x = 0;
                    wave[0].innerHTML = this.data.playing[0][x];
                    wave[1].innerHTML = this.data.playing[1][x];
                    wave[2].innerHTML = this.data.playing[2][x] 
                }
            }, 150)
        }
    },
    mounted() {
        this.startWaveform();
    },
    created() {
        this.$watch('currentRadio', () => {
            this.$refs.player.load();
            this.playing = true;
        })
    }
}
</script>

<style lang="scss" scoped>
    .player {
        background-color: #fff;
        border: 3px #282828 solid;
        border-right: 6px #282828 solid;
        border-bottom: 6px #282828 solid;
        font-family: "IBM Plex Mono", monospace;
        .heading {
            display: flex;
            justify-content: space-between;
            background-color: #ff45b4;
            border-bottom: 2px solid #282828;
        }
        .audio-wave {
            .wave-1 {
                color: #b462ff
            }
            .wave-2 {
                color: #ff45b4;
            }
            .wave-3 {
                color: #18b6ff
            }
            .wave-inactive {
                opacity: 0;
            }
        }
        .controls {
            .play {
                background-color: #4FFEAE;
                border: 2px #282828 solid;
                border-right: 5px #282828 solid;
                border-bottom: 5px #282828 solid;
                border-radius: 8px;
            }
            .play:hover {
                cursor: pointer;
            }
            .name {
                color: #282828;
            }
        }
    }
    
    @media only screen and (max-width: 600px) {
        .player {
            margin: 30px auto;
            width: 330px;
            border-radius: 8px;
            line-height: 14px;
            .heading {
                padding: 15px 15px;
                margin-bottom: 30px;
            }
            .audio-wave {
                padding: 10px 20px;
                .wave {
                    font-size: 20px;
                }
            }
            .controls {
                display: flex;
                align-items: center;
                margin: 10px 0px;
                padding: 10px 20px;
                .play {
                    padding: 10px;
                    margin-right: 5px;
                    width: 12px;
                }
                .name {
                    margin: 0px 5px;
                }
            }
        }
    }
    
    @media only screen and (min-width: 600px) and (max-width: 800px) {
        .player {
            margin: 10px auto;
            width: 500px;
            border-radius: 6px;
            .heading {
                padding: 15px 15px;
                align-items: center;
                .title {
                    font-size: 20px;
                }
            }
            .audio-wave {
                line-height: 24px;
                padding: 20px 20px;
                .wave {
                    font-size: 32px;
                }
            }
            .controls {
                display: flex;
                padding: 10px 20px;
                align-items: center;
                .play {
                    padding: 8px;
                    width: 30px;
                    text-align: center;
                    margin-right: 10px;
                    font-size: 24px;
                }
                .name {
                    margin: 0px 10px;
                    font-size: 18px;
                }
            }
        }
    }

    @media only screen and (min-width: 800px) {
        .player {
            margin: 10px auto;
            width: 500px;
            border-radius: 6px;
            .heading {
                padding: 15px 15px;
                align-items: center;
                .title {
                    font-size: 20px;
                }
            }
            .audio-wave {
                line-height: 24px;
                padding: 20px 20px;
                .wave {
                    font-size: 32px;
                }
            }
            .controls {
                display: flex;
                padding: 10px 20px;
                align-items: center;
                .play {
                    padding: 8px;
                    width: 30px;
                    text-align: center;
                    margin-right: 10px;
                    font-size: 24px;
                }
                .name {
                    margin: 0px 10px;
                    font-size: 18px;
                }
            }
        }
    }
</style>