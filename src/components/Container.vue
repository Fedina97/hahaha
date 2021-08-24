<template>
  <div class="container">
    <ClientForm/>
  </div>
</template>

<script>
import ClientForm from '@/components/Form/Form.vue'

export default {
  name: 'Container',
  components:{
    ClientForm
  }
}
</script>

<style lang="sass">
  .container
    background: url(../assets/02.03.18_medicina.jpg) center center/ cover no-repeat
    height: 100vh
    display: flex
    align-items: center
    justify-content: center    
</style>


