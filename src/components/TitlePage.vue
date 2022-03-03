<template>
    <div class="banner bg-gradient-a1-a2">
        <div class="container text-center fg-color-dark">
            <h1>{{title}}</h1>
            <hr>
            <p>{{description}}</p>
            <button class="primary" v-on:click="start">Start</button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        title: {
            type: String,
            required: true
        },
        description: {
            type: String,
            required: true
        }
    },
    methods: {
        start: function(e) {
            this.$emit("start");
        }
    }
}
</script>
