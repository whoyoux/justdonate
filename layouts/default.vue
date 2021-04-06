<template>
  <div>
    <Header />
    <Nuxt />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
export default {
  components: {
    Header
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Quando&display=swap");

:root {
  --color-primary: #e05050;
}

body {
  font-family: "Quando", serif;
  font-size: 16px;
  margin: 0;
  padding: 0;
  color: #000;
}

/* .button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}*/
</style>
