<template>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h2>{{ user.age }}</h2>
    <button @click="setAge">Change Age</button>
  </section>
</template>

<script>
// import { ref } from 'vue'; // ref is always used for things like strings and numbers and even objects but takes more work with objects (to include .value)
import { reactive } from 'vue'; // reactive ONLY works with objects

export default {
  setup() {
    // const uName = ref('Justin');
    // const uAge = ref(31);

    const user = reactive({
      name: 'Justin',
      age: 31
    })

    console.log(user);

    // setTimeout(function() {
    //   // uName.value = 'Just';
    //   // uAge.value = 32;
    //   user.name = 'Just';
    //   user.age = 32;
    // },2000)

    function setNewData() {
      user.age = 32;
    }

    return {
      user: user,
      setAge: setNewData
    };
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