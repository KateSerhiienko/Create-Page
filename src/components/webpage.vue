<template>
  <div class="webpage" :style="`backgroundColor: ${webpageProperties.backgroundColor}; color: ${ webpageProperties.textColor}`">
    <h1>{{ webpageProperties.header }}</h1>
    <main>
      <div class="main__img">
        <img :src="webpageProperties.img">
      </div>
      <div class="main__info">
        <p><span>Name: </span>{{ webpageProperties.name }}</p>
        <p><span>Age: </span> {{ webpageProperties.age }}</p>
        <p><span>Profession: </span> {{ webpageProperties.profession }}</p>
      </div>
      <p>{{ webpageProperties.information }}</p>
    </main>
  </div>
</template>

<script>
export default {
  name: 'webpage',
  props: {
    webpageProperties: Object
  }
}
</script>

<style scoped lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans&display=swap');

  .webpage {
    border: 1px solid grey;
    padding: 4vw;
    font-family: 'Open Sans', sans-serif;
    font-size: 1.8vw;
  }
  h1{
    text-align: center;
    text-transform: uppercase;
    margin: 0;
    margin-bottom: 3vw;
  }
  main {
    display: grid;
    grid-template-columns: 5fr 3fr;
    grid-gap: 3vw;
    p {
      grid-column: 1/3;
    }
  }
  .main__img {
    display: flex;
    box-shadow: .8vw .8vw 1vw grey;
    img{
      width: 100%;
    }
  }
  .main__info {
    span{
      display: inline-block;
      width: 8vw;
      font-size: 1.3vw;
      opacity: .6;
    }
  }
</style>