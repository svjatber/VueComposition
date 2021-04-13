<template>
  <section>
    <h2>{{userName}}</h2>
    <h2>{{age}}</h2>
  </section>
</template>

<script>
import {computed,
        inject,
        onBeforeMount,
        onMounted,
        onBeforeUpdate,
        onUpdated,
        onUnmounted
                } from 'vue'
export default {
  props: ['lastName', 'firstName', 'age'],
  setup(props){
    const uName = computed(function() {
      return props.firstName + props.lastName
    })

    console.log('aaaaa')

    onBeforeMount(()=>{
      console.log('onBeforeMount')
    })

    onMounted(()=>{
      console.log('onMount')
    })

    onBeforeUpdate(()=>{
      console.log('onBeforeUpdate')
    })

    onUpdated(()=>{
      console.log('onUpdated')
    })

    onUnmounted(()=>{
      console.log('onUnmounted')
    })



    // context.emit(); // this.$emit('save-data', 1)
    const user = inject('userName')
    console.log(user)
    return{
      userName: uName
    }
  }
}
</script>

<style scoped>

</style>
