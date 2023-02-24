<template>
  <footer>
    Made with <span>❤</span> by Rohit 
  </footer>
</template>

<script>
export default {
    name: "FooterLayout"
}
</script>

<style lang="scss" scoped>
    footer {
        font-family: "IBM Plex Sans", monospace;
        text-align: center;
        padding: 4px;
        background-color: #282828;
        color: #fff;
        span {
            font-family: system-ui, sans-serif;
            color: #db0000;
        }
    }
</style>