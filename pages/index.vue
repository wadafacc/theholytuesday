<template>
  <div class="main">
    <div class="head">
      <h1>THE HOLY TUESDAY</h1>
      <h5>the only menu you'll ever need.</h5>
      <i><h5>[siemens exclusive, for now]</h5></i>
    </div>
    <div v-for="day in menu" :key="day.title" class="menu-container">
      <h2 class="title">
        {{ day.category }} | <span class="highlight">{{ day.title }}</span>
      </h2>
      <h3>{{ day.description }}</h3>
      <h4 class="price">CHF {{ day.price }}</h4>
    </div>
  </div>
</template>

<style src="~/styles/global.css">
</style>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      menu: [],
    };
  },
  mounted() {
    this.$axios
      .get("https://api.fivemoods.ch/menu/")
      .then((res) => {
        res.data.forEach((e) => {
          if (e.weekday.toLowerCase() === "tuesday") {
            this.menu.push(e);
            console.log(e);
          }
        });
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
