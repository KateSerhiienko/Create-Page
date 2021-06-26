<template>
  <div class="wrapper">
    <toolbar
      @setBackgroundColor="setBackgroundColor"
      @setTextColor="setTextColor"
      @setHeader="setHeader"
      @setName="setName"
      @setAge="setAge"
      @setProfession="setProfession"
      @setInformation="setInformation"
      @setPhoto="setPhoto"
    />
    <webpage
      :webpageProperties="webpageProperties"
    />
  </div>
</template>

<script>
import toolbar from './toolbar'
import webpage from './webpage'

export default {
  name: 'wrapper',
  components: {
    toolbar,
    webpage
  },
  data() {
    return {
      webpageProperties: {
        backgroundColor: "#ffffff",
        textColor: "#333333",
        header: "Header",
        name: "",
        age: "",
        profession: "",
        information: "Some text",
        img: require("../assets/img/stubImage.png")
      }
    }
  },
  methods: {
    setBackgroundColor(value) {
      this.webpageProperties.backgroundColor = value;
    },
    setTextColor(value) {
      this.webpageProperties.textColor = value;
    },
    setHeader(value) {
      this.webpageProperties.header = value;
    },
    setName(value) {
      this.webpageProperties.name = value;
    },
    setAge(value) {
      this.webpageProperties.age = value;
    },
    setProfession(value) {
      this.webpageProperties.profession = value;
    },
    setInformation(value) {
      this.webpageProperties.information = value;
    },
    setPhoto(value) {
      this.webpageProperties.img = value;
    },
  },
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
  }
  :active, :hover, :focus {
    outline: 0;
    outline-offset: 0;
  }
  .wrapper {
    display: grid;
    grid-template-columns: 2fr 6fr;
    grid-gap: 2vw;
    margin: 2vw;
  }
</style>