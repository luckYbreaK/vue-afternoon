<template>
  <div>

    <nav>
      <button @click="toggle('create')">Create</button>
      <h1>Battle Bots</h1>
      <button @click="toggle('collection')">Collection</button>
    </nav>

    <section v-if="showCreate">
      <create :createBot="createBot"/>
    </section>


    <section v-else>
      <bot-list :botList="botList"/>

    </section>
    


  </div>
</template>

<script>
import Create from "./components/Create";
import BotList from "./components/BotList";

export default {
  data() {
    return {
      showCreate: true,
      botList: []
    }
  },
  methods: {
    toggle(val) {
      this.showCreate = val === "create" ? true : false;
    },
    createBot(name, attack, health) {
      let bot = {
        name: name,
        attack: attack,
        health: health
      }
      this.botList.push(bot);
    }
  },
  components: {
    Create,
    BotList
  }
};
</script>

<style>
nav {
  display: flex;
  justify-content: space-around;
}
</style>
