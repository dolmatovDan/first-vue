<template>
    <div class="page">
      <h2>Random Activity</h2>
      <div v-show="property" v-for="(property, index) in data" v-bind:key="index" class="element text">
        {{index}} : {{ property }}
      </div>
      <a class="link text " v-if="'link' in activities" :href="activities.link">Follow the link</a>
      <br>
      <button @click="getAcivity" class="button"> Change</button>
    </div>

</template>

<script>


export default {
  props: {
    data: Object,
  },
  name: "CardVue",

  
  data: function() {
    return {
      users: ['0zguner', '3imed-jaberi', 'a0viedo', 'AbeEstrada', 'ak239'],
      activities: [],
    }
  },
  methods: {
    getAcivity() {
      this.$emit('addcard');
    },
  }
};
</script>

<style scoped>
  .pages {
    margin-right: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    background-color: #f4f4f4;
    padding: 20px;
  }

  h2 {
    color: rgb(65, 64, 64);
  }

  .element {
    padding: 15px 10px;
    background-color: #fff;
    border-radius: 5px;
  }
  .button {
    background-color: transparent;
    padding: 10px 15px;
    border: 1px solid black;
    margin-top: 15px;
    font-size: 16px;
    cursor: pointer;
    border-radius: 5px;
  }

  .button:hover {
    background-color: #fff;
  }

  .link {
    text-decoration: none;
    color: rgb(0, 0, 0);
    padding: 15px 10px;
  }

  .link:hover {
    text-decoration: underline;
  }

  .text {
    font-size: 18px;
    margin-bottom: 15px;
    color: rgb(66, 66, 66);
  }
</style>
