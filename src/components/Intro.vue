<template>
  <div class="intro">
    <h1>{{lang.title[0]}} <span>radio's</span> {{lang.title[1]}}</h1>
	<p>{{lang.subtitle}}</p>
    <div class="request">
        <a href="mailto:rohitjethoe@proton.me">{{ lang.request }}</a>
    </div>
  </div>
</template>

<script>
export default {
    name: "IntroComponent",
    props: {
        lang: JSON
    }
}
</script>

<style lang="scss" scoped>
	.intro {
		font-family: "IBM Plex Sans", monospace;
		h1 {
			font-weight: 500;
			span {
				background-color: #b462ff;
				padding: 2px 8px;
			}
		}
		p {
			font-weight: 400;
			color: #4D4D4D;
		}
        .request {
            a:link, a:visited {
                color: #282828;
                text-decoration: none;
                background-color: #4FFEAE;
                border: 2px #282828 solid;
                border-right: 4px #282828 solid;
                border-bottom: 4px #282828 solid;
                border-radius: 4px;
                text-transform: uppercase;
                font-weight: 500;
                padding: 6px 10px;
            }
        }
	}

	@media only screen and (max-width: 600px) {
		.intro {
			width: 90%;
			margin: 0px auto;
			padding: 20px 0px;
			text-align: center;
			h1 {
				text-align: center;
				font-size: 24px;
				margin: 10px 0px;
			}
			p {
				margin: 10px 0px;
				font-size: 16px;
			}
            .request {
                margin-top: 25px;
            }
		}
	}

    @media only screen and (min-width: 600px) and (max-width: 800px) {
        .intro {
            width: 500px;
            text-align: center;
            margin: 0px auto;
            padding: 20px 0px;
            padding-bottom: 40px;
            h1 {
                font-size: 30px;
                margin: 10px 0px;
            }
            p {
                margin: 10px 0px;
            }
            .request {
                margin-top: 25px;
            }
        }
    }

    @media only screen and (min-width: 800px) {
        .intro {
            width: 500px;
            text-align: center;
            margin: 0px auto;
            padding: 20px 0px;
            padding-bottom: 40px;
            h1 {
                font-size: 30px;
                margin: 10px 0px;
            }
            p {
                margin: 10px 0px;
            }
            .request {
                margin-top: 25px;
            }
        }
    }
</style>
