<template>
  <div class="select">
    <div class="radios">
      <div class="radio" v-for="item in countries" v-bind:key="item">
        <div class="radio-country">
          {{  lang.countries[item.toUpperCase()] }}
        </div>
        <div class="radio-item" v-for="item in data[item]" v-bind:key="item">
          <a @click="$event => changeRadio(item.id, item.country)">{{ item.name }}</a>
        </div>
      </div>
      <div class="radio">
        <div class="radio-country">
          {{ lang.extra.title }}
        </div>
        <div class="radio-item available-soon">
          {{ lang.extra.subtitle }}
        </div>
    </div>
   </div> 
  </div>
</template>

<script>
export default {
    name: "SelectComponent",
    data() {
      return {
        countries: {
          0: 'nl',
          1: 'in',
          2: 'jp'
        }
      }
    },
    props: {
      data: JSON, lang: JSON
    },
    methods: {
      changeRadio: function (id, country) {
        const radio = {
          id: id,
          country: country
        }

        this.$emit('changeRadio', radio);
      }
    }
}
</script>

<style lang="scss" scoped>
  .select {
    margin-top: 50px;
    background-color: #f1f7f2;
    .radio {
      .radio-country {
        font-weight: 600;
        background-color: #fff;
        border: 2px #282828 solid;
        border-right: 4px #282828 solid;
        border-bottom: 4px #282828 solid;
      }
      .radio-item {
        font-family: "IBM Plex Mono", monospace;
        color: #282828;
      }
      .radio-item:hover {
        cursor: pointer;
        color: #b462ff;
      }
      .available-soon:hover {
        cursor: default;
        color: #282828;
      }
    }
  }

  @media only screen and (max-width: 600px) {
    .select {
      padding: 40px 0px;
      .radio {
        width: 80%;
        margin: 20px 20px;
        .radio-country {
          width: 200px;
          padding: 8px 8px;
        }
        .radio-item {
          padding: 8px 8px;
        }
      }
    }
  }

  @media only screen and (min-width: 600px) and (max-width: 800px) {
    .select {
      padding: 40px 0px;
      .radio {
        width: 80%;
        margin: 20px 40px;
        .radio-country {
          width: 300px;
          padding: 8px 8px;
          font-size: 20px;
        }
        .radio-item {
          padding: 8px 8px;
          font-size: 18px;
        }
      }
    }
  }

  @media only screen and (min-width: 800px){
    .select {
      padding: 40px 0px;
      .radios {
        width: 800px;
        margin: 0 auto;
      }
      .radio {
        width: 80%;
        margin: 20px 40px;
        .radio-country {
          width: 300px;
          padding: 8px 8px;
          font-size: 20px;
        }
        .radio-item {
          padding: 8px 8px;
          font-size: 18px;
        }
      }
    }
  }
</style>