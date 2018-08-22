<template>
        <div class="bot_container">
            <h1>{{bot.name}}</h1>
            <h2>Attack: {{bot.attack}}</h2>
            <h2>Health: {{bot.health}}</h2>
            <div class="btn_container">
                <button @click="selectBot(bot.name)">Select</button>
                <button @click="retireBot(index)">Retire</button>
            </div>      
        </div>
</template>


<script>
export default {
  props: ["bot", "index", "retireBot", "selectBot"]
};
</script>

<style>
.bot_container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.btn_container {
  display: flex;
  justify-content: center;
}
</style>

