<!-- <script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from '@/components/HelloWorld.vue'
</script> -->

<template>
<Header/>
<div class="container mx-auto">
<router-view></router-view>
</div>
</template>

<script>
import Header from './components/Header.vue'
export default {
  components:{
    Header
  }
  
}
</script>
