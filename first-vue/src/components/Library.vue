<template>
  <div class="library" id="library" >

    <div  class="pages" v-for="(activity, key) in activities" v-bind:key="key">
      <CardVue v-on:addcard="getAcivity" :data="activity" />
    </div>
  </div>
</template>

<script>
import CardVue from "./CardVue";

export default {
  components: {
    CardVue,
  },
  name: "Library",
  created: function () {
      this.getAcivity();
  },
  data: function() {
    return {
      users: ['0zguner', '3imed-jaberi', 'a0viedo', 'AbeEstrada', 'ak239'],
      activities: [],
    }
  },
  methods: {
    computedURLs() {
      return ['https://www.boredapi.com/api/activity', 'https://api.github.com/users/' + this.getPeople()]
    },
    getAcivity() {
      let link = this.computedURLs()[Math.trunc(Math.random() * this.computedURLs().length)];
      fetch(link)
      .then(response =>  response.json())
      .then(data => this.activities.push(this.formatObj(data)));
    },
    getPeople() {
      return this.users[Math.trunc(Math.random() * this.users.length)];
    },
    formatObj(obj) {
      let resObj = {};
      for (let key in obj) {
        if (obj[key]) {
          resObj[key] = obj[key];
        }
      }
      return resObj;
    }
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

  .library {
    padding: 15px;
    background-color: rgb(130, 168, 219);
    font-size: 16px;
    width: 100vw;
    border-radius: 5px;
    overflow: auto; 
    display: flex;
    flex-wrap: wrap;
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
