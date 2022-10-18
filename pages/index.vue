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
      <div class="desc">
        <h3>{{ day.description }}</h3>
      </div>
      <div class="price">
        <h4>
          CHF {{ day.price }} / {{ (day.price * 0.75).toFixed(1) + 0 }} (-25%)
        </h4>
      </div>
    </div>
    <div class="footer">
      <h5>
        made with ❤ by
        <a
          href="https://github.com/wadafacc"
          target="_blank"
          rel="noopener noreferrer"
          >functionizable</a
        >
      </h5>
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
      .get("https://api-prod.fivemoods.ch/menu/day/tuesday")
      .then((res) => {
        this.menu = res.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
