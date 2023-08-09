<template>
 <News/>
</template>

<script>
import axios from 'axios';

export default {  
  data() {
    return {
      data: null,
      TitleBlog: 'Super News',
      news_text: 'i.news_text'
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

