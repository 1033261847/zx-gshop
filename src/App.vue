<template>
  <div id="app">
    	<router-view />
    	<FooterGuide v-show="$route.meta.showFooter"/>
  </div>
</template>

<script>
import FooterGuide from './components/FooterGuide/FooterGuide.vue'	

/*import {reqGetListCitys} from './api'*/

export default {
  name: 'App',
  components: {
		FooterGuide
  },
  /*async mounted(){
  	const result=await reqGetListCitys('getListCitys')
  	console.log(result)
  }*/
  
  mounted(){
  	 //this.$store.dispatch('getListCitys')
  }
  
}
</script>

<style>
#app {
	width: 100%;
	height: 100%;
	background: #f5f5f5;
  
}
</style>
