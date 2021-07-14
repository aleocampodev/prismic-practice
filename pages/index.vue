<template>
 <div>
   hola
   <div>
    <h1 v-text="data.title[0].text"></h1>
    <p v-text="data.text[0].text"></p>
    <div>{{data.body[0].items[0].image.url}}</div>
    <img :src="data.image.url"/>
    <v-carousel>
      <v-carousel-item
        v-for="(item,i) in items"
        :key="i"
        :src="item.src"
        reverse-transition="fade-transition"
        transition="fade-transition"
      ></v-carousel-item>
    </v-carousel>
  </div>
 </div>
</template>

<script>
export default {
  async asyncData({$prismic}){
    const  data  = await $prismic.api.getSingle('oso_panda');
    console.log("Hola soy la data", data)
     return  data 
  },
  data () {
      return {
        items: [
          {
            src:'https://cdn.vuetifyjs.com/images/carousel/sky.jpg',
          },
          {
            src: 'https://cdn.vuetifyjs.com/images/carousel/sky.jpg',
          },
          {
            src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
          },
          {
            src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
          },
        ],
      }
    }
}
</script>
