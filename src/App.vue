<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h2>{{ age }}</h2>
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First Name" @input="setFirstName"/>
      <input type="text" placeholder="Last Name" @input="setLastName"/>
    </div>
  </section>
</template>

<script>
import { ref, computed } from 'vue'; // ref is always used for things like strings and numbers and even objects but takes more work with objects (to include .value)
// import { reactive } from 'vue'; // reactive ONLY works with objects

export default {
  setup() {
    // const uName = ref('Justin');
    const uAge = ref(31);
    const firstName = ref('');
    const lastName = ref('');

    const uName = computed(function() {
      return firstName.value + ' ' + lastName.value
    });

    // const user = reactive({
    //   name: 'Justin',
    //   age: 31
    // })

    // setTimeout(function() {
    //   // uName.value = 'Just';
    //   // uAge.value = 32;
    //   user.name = 'Just';
    //   user.age = 32;
    // },2000)

    function setNewData() {
      uAge.value = 32;
    }

    function setFirstName(event) {
      firstName.value = event.target.value;
    }

    function setLastName(event) {
      lastName.value = event.target.value;
    }

    return { 
      userName: uName, 
      age: uAge, 
      setNewData, 
      setFirstName, 
      setLastName}
  }
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
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