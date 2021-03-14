<template>
  <div class="console">
    <div class="commands-place" id="commands-place">
      <div
        v-for="(command, key) in enteredCommands"
        v-bind:key="key"
        class="command-item"
      >
        {{ command }}
      </div>
      <div
        v-for="(command, key) in showCommands"
        v-bind:key="'showKey' + key"
        class="command-item"
      >
      {{ command }}
      </div>
      
      <br />
    </div>
    <label for=""><input v-model="command" @keydown.13="addCommand" id="command" type="text" /></label>
  </div>
</template>

<script>
export default {
  name: "Console",
  props: {
    msg: String,
    text: String,
  },
  data: function () {
    return {
      command: '',
      showCommands: [],
      commands: [
        "clear — очищает консоль",
        "print — выводит текст на экран",
        "time — выводит текущее время",
      ],
      enteredCommands: [],
    };
  },
  
  methods: {
    helpCommand: function() {
      this.enteredCommands.push(...this.commands);
    },
    clearCommand: function() {
      this.enteredCommands.length = 0;
    },
    printCommand: function(text) {
      alert(text);
    },
    timeCommand: function() {
      let date = new Date();
      this.enteredCommands.push(date.getHours().toString() + ':' + date.getMinutes().toString()); 
    },
    addCommand: function() {
      this.enteredCommands.push("admin@chat: " + this.command);
      switch(this.command){
        case 'help':
          this.helpCommand();
          break;
        case 'clear':
          this.clearCommand();
          break;
        case 'time':
          this.timeCommand();
          break;
        default:
          this.enteredCommands.push('"' + this.command + '" не является встроенной функцией')
          break;

      }
      this.command = "";
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.console {
  width: 400px;
  height: 400px;
  background-color: black;
  padding: 15px;
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  align-items: flex-start;
}


input {
  color: #fff;
  background-color: transparent;
  font-size: 16px;
  border: none;
  width: 100%;
  outline: none;
  flex-grow: 1;
}

label {
  display: flex;
  width: 100%;
}

label::before {
  display: inline-block;
  content: "admin@chat:";
  font-size: 16px;
  color: #fff;
  margin-right: 7px;
}

.command-item {
  color: #fff;
  line-height: 2;
}
</style>
