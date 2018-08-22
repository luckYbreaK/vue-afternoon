<template>
    <div>
        <section class="header">
            <h1>Bot #1: {{bot1}}</h1>
            <h1>Bot #2: {{bot2}}</h1>
            <div>
                <button @click="battle" :disabled="disabled">Battle</button>
                <button @click="clearBots">Clear</button>
            </div>
        </section>
        <hr>

        <section class="bot_list">
            <bot v-for="(bot, i) in botList" :key="i" :bot="bot" :index="i" :retireBot="retireBot" :selectBot="selectBot"/>
        </section>
        
    </div>
</template>

<script>
import Bot from "./Bot";

export default {
  data() {
    return {
        bot1: "Select a bot below",
        bot2: "Select a bot below",
        count: 0,
        disabled: true
    };
  },
  methods: {
    retireBot(index) {
      this.botList.splice(index, 1);
    },
    selectBot(name) {
        this.count += 1;
        if(this.count === 1) {
            this.bot1 = name
        }else if(this.count === 2) {
            this.bot2 = name
            this.disabled = false;
        }
    },
    clearBots() {
        this.bot1 = "Select a bot below";
        this.bot2 = "Select a bot below";
        this.disabled = true;
    },
    battle() {
        let random = Math.floor(Math.random() * 2) + 1;
        random === 1 ? alert(`${this.bot1} wins!`) : alert(`${this.bot2} wins!`)
    }
  },
  props: ["botList"],
  components: { Bot }
};
</script>

<style>
.header {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.btn_container {
  display: flex;
  justify-content: center;
}
.bot_list {
  display: flex;
  justify-content: space-around;
}
</style>


