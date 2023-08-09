<template>
  <div class='w-3/5 mx-auto my-20' id="container">
    <h1 class='text-3xl font-semibold text-red-600'>{{TitleBlog}}</h1>
    
    <div v-if="data" class='mx-auto my-10 grid grid-cols-3 gap-10'>
      <div class='' v-for='(i, index) in data' :key="index">
        <!-- <div>          <h2 class='text-5xl font-semibold mb-5'>{{ i.news_title }}</h2> -->
          <div>        
            <header class="">
              <h2>{{ i.category }}</h2>
            </header>
            <div>
            <a href="">
            <figure>
              <img :src='i.news_image' class="w-full">
             <figcaption>{{i.news_subtitle}}</figcaption>
             <br/>
             <h6>{{i.news_font}}</h6>
            </figure>
            </a>
          </div>         
        </div>
        
                 
        <!-- <div v-html='i.news_text'></div> -->        
      </div>        
    </div>
  </div>  
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      data: null,
      TitleBlog: 'Super News'      
    };
  },
  created(){
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const response = await axios.get('https://www.megasistema.app.br/api/diario-fm/news');
        this.data = response.data.data;

      console.log(response.data.data)
    }
    
  }
};
</script>