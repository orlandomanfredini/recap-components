<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
import AppCard from './components/AppCard.vue';

export default {
  components: {
    AppCard,
  },



  data(){
    return{
      myCard: [],
      

    }
  },

  methods:{
    fetchCard(){
      const n = 5;

      // objectCard= {

      // };


      for(let i = 0; i < n; i++){
        axios.get('https://api.scryfall.com/cards/random')
        .then((res)=>{
        const data = res.data
        // console.log(data.name, data.image_uris.normal);
        const name = data.name;
        const src = data.image_uris.normal;

        // console.log(name, src);

        

        this.myCard.push({
          nameCard: name,
          img: src,

        });

        
      })
      
      }
      
      
    }
  },

  mounted(){
    this.fetchCard()
    
  }
}
</script>

<template>
  <h1>Hello world</h1>
  
  <div v-for="(card, i) in myCard" class="info-card">
    <AppCard :nameCard="card.nameCard" :img="card.img"/>
  </div>
</template>

<style lang="scss" scoped>
.info-card{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
  padding: 20px;


  img{
    max-width: 300px;
  }


}

</style>
