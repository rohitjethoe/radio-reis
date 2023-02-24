<template>
    <header>
        <div 
        v-bind:class="navHandler ? 'nav-opened' : ''"
        class="navigation"
        >
            <div 
            @click="$event => openNavigation()"
            class="burger-icon"
            >
                <div class="bar bar-1"></div>
                <div class="bar bar-2"></div>
            </div>
            <ul>
                <li>
                    <a href="">
                        {{ lang.navigation.home }}
                    </a>
                </li>
                <li>
                    <a href="">
                        {{ lang.navigation.about }}
                    </a>
                </li>
            </ul>
        </div>
        <div class="logo">
            <a href="./">
                Radio Reis
            </a>
        </div>
        <div class="languages">
            <a 
            v-bind:class="currentLang == 'nl' ? 'active' : ''" @click="$event => changeLanguage('nl')"
            >
                NL
            </a>
            /
            <a 
            v-bind:class="currentLang == 'en' ? 'active' : ''" @click="$event => changeLanguage('en')"
            >
                EN
            </a>
        </div>
    </header>
</template>

<script>
import langNL from '../languages/nl.json';
import langEN from '../languages/en.json';

export default {
    name: "HeaderLayout",
    data() {
        return {
            currentLang: "nl",
            lang: langNL.header,
            navHandler: false
        }
    },
    methods: {
        changeLanguage: function (lang) {
            document.querySelector("#main").setAttribute("lang", lang);
            this.currentLang = lang;
            lang == "nl" ? this.lang = langNL.header : this.lang = langEN.header;
        },
        openNavigation: function () {
            this.navHandler = !this.navHandler
        }
    }
}
</script>

<style lang="scss" scoped>
    header {
        background-color: #FFF;
        border-bottom: 3px solid #282828;
        user-select: none;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        -khtml-user-select: none;
        -webkit-touch-callout: none;
        .logo {
            font-weight: 500;
            text-transform: uppercase;
            a:link, a:visited { 
                color: #fff;
                -webkit-text-stroke: 1px #282828;
                text-shadow: 2px 2px 0 #282828;
                font-family: 'IBM Plex Sans', sans-serif;
                text-decoration: none;
            }
        }
        .navigation {
            ul {
                li {
                    list-style-type: none;
                    a:link, a:visited {
                        font-family: 'IBM Plex Mono', monospace;
                        text-decoration: none;
                        color: #282828;
                    }
                }
            }
            .burger-icon {
                .bar {
                    width: 20px;
                    margin: 4px 0px;
                    height: 3px;
                    border-radius: 4px;
                    background-color: #282828;
                    transition: 0.25s;
                }
            }
            .burger-icon:hover {
                cursor: pointer;
            }
        }
        .languages {
            font-family: 'IBM Plex Mono', monospace;
            a {
                transition: 0.25s;
            }
            a:hover {
                cursor: pointer;
            }
            .active {
                color: #4FFEAE;
                font-weight: 600;
            }
        }
    }

    @media only screen and (max-width: 600px) {
        header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px 15px;
            .logo {
                font-size: 30px;
            }
        }
        .navigation {
            .burger-icon {
                padding: 8px;
            }
            ul {
                z-index: 0;
                position: absolute;
                top: 0;
                left: 0;
                margin-top: 62.5px;
                transform: translateY(-500px);
                li {
                    background-color: #f8f8f8;
                    width: calc(100vw - 20px);
                    padding: 10px;
                }
            }
        }
        .nav-opened {
            .burger-icon {
                background-color: #f8f8f8;
            }
            ul {
                transform: translateY(0px);
            }
        }
    }

    @media only screen and (min-width: 600px) and (max-width: 800px) {
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            .logo {
                font-size: 32px;
                flex-grow: 2;
            }
            .navigation {
                flex-grow: 1;
                .burger-icon {
                    display: none;
                }
                ul {
                    li {
                        margin: 0px 10px;
                        display: inline;
                    }
                }
            }
        }
    }

    @media only screen and (min-width: 800px) {
        header {
            width: 800px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            border-bottom: none;
            .logo {
                font-size: 32px;
                flex-grow: 2;
            }
            .navigation {
                flex-grow: 1;
                .burger-icon {
                    display: none;
                }
                ul {
                    li {
                        margin: 0px 15px;
                        display: inline;
                    }
                }
            }
        }
    }
</style>