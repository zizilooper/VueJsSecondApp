<template>
  <div>
    <h4>Active users:</h4>

    <h2>{{ users }}</h2>
    <!-- <h2>{{ loginN}}</h2> -->

   

  </div>
</template>

<script>
export default {
  name: "Visit",
  props: {
    users: {
      default: "users",
    },
    loginN:{}


  },
  data() {
    return {
      counter: "",
    };
  },
};
</script>

<style></style>
