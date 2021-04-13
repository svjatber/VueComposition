<template>
  <section class="container">
    <user-data :last-name="inputName" :first-name="inputLast" :age="age" ></user-data>
    <button @click="setNewData">Click</button>
    <input type="text" placeholder="First Name" v-model="inputName">
    <input type="text" placeholder="Last Name" ref="lastNameInput">
    <button @click.prevent="setLastName"> Set Last Name</button>
  </section>
</template>

<script>
import { reactive , toRefs, ref, provide} from "vue";
import UserData from "@/components/UserData";



export default {
  components: {
    UserData
  },
  setup(){

    // const UserName = ref('aaaa')
    // ref.value

    const inputName = ref('Svjat')
    const inputLast = ref('Bereziuk')
    const lastNameInput = ref('')

    console.log(inputLast)
    console.log(inputName)

    const userName = reactive({
      name: 'Maxilian',
      age: 31
    })

    // const AllName = computed(() =>{
    //   return inputName.value + ' ' + inputLast.value
    // })

    // const setInputName = (e) => {
    //   inputName.value = e.target.value
    // }
    // const setInputLast = (e) => {
    //   inputLast.value = e.target.value
    // }
    // setTimeout(()=>{
    //   // UserName.value
    //   userName.name = 'Max2'
    //   userName.age = 25
    // },1000)


    // watch(inputName, (newValues)=>{
    //   inputName.value = 'old age:' + newValues
    // })

    const setNewData = () => {
      userName.age = 32
    }


    const setLastName = () =>{
      inputLast.value = lastNameInput.value.value
      console.log(lastNameInput)
    }

    provide('userName', userName)

    const userRefs = toRefs(userName)
    return {
      name: userRefs.name,
      age: userRefs.age,
      inputLast,
      inputName,
      setLastName,
      lastNameInput,
      setNewData
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
