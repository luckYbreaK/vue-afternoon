<template>
    <div>
        <form @submit.prevent="clearForm">
            <input type="text" placeholder="Bot Name*" v-model="name"/>
            <input type="number" placeholder="Attack Value*" v-model="attack"/>
            <input type="number" placeholder="Health Value*" v-model="health"/>
            <div class="btn_container">
                <button type="submit" @click="createBot(name, attack, health)" :disabled="(name === '' || attack === '' || health === '')">Submit</button>
                <button>Clear</button>
            </div>          
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: "",
            attack: "",
            health: "",
            disabled: true
        }
    },
    methods: {
        clearForm() {
            this.name = "",
            this.attack = 0,
            this.health = 0
        }
    },
    computed: {
        disableButton : () => this.name && this.attack && this.health
    },
    props: ["createBot"]
}
</script>

<style>
form {
    display: flex;
    flex-direction: column;
}
.btn_container {
    display: flex;
    justify-content: center;
}
</style>


