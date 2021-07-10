<template>
 <div>
   <div>
    <h1 v-text="data.title[0].text"></h1>
    <p v-text="data.text[0].text"></p>
    
    <img :src="data.image.url"/>
  </div>
 <div>
   <h3 v-text="data.title[0].text"></h3>
 </div>
 </div>
</template>

<script>
export default {
 async asyncData( {$prismic}){
     const {data} = await $prismic.api.getSingle('simplepage');
    console.log("Hola soy la data", data)
     return  {data }
  }
}
</script>
