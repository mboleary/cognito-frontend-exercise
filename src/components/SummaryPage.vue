<template>
    <div>
        <div class="title-banner bg-gradient-a3-a4">
            <div class="container text-center">
                <h1>Response Summary</h1>
                <hr>
                <p>Here are your results</p>
            </div>
        </div>
        <main>
            <div class="container">
                <div class="content-card full-width boxfix" v-for="question of questions" :key="question.id">
                    <h3>{{question.text}}</h3>
                    <p><b>{{question.response}}</b></p>
                </div>
                <hr>
                <button class="tertiary accent-4" v-on:click="handleClick">Take again</button>
            </div>
        </main>
    </div>
</template>

<script>
export default {
    props: {
        questions: {
            type: Array,
            required: true
        }
    },

    methods: {
        handleClick () {
            this.$emit("restart");
        }
    }
}
</script>

<style scoped>
    .boxfix {
        box-sizing: border-box;
    }
</style>