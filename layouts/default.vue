<template>
  <div>
    <Header />
    <div class="bg-indigo-100 py-8">
      <div class="main__container">
        <nuxt/>
      </div>
    </div>
    <Footer/>
  </div>
</template>
<script>
import Header from '../layouts/partials/header.vue';
import Footer from '../layouts/partials/footer.vue';

export default ({
    components:{Header,Footer},
    methods:{

    },
    mounted(){
       
      console.log("layout mount");
      const token = localStorage.getItem('token')
       if(token){
          this.$store.commit('SET_AUTHENTICATED',true);
       };

       this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => this.$nuxt.$loading.finish(), 500)
    })
    }
})
</script>

<style>
body{
    overflow-x: hidden;
}
</style>