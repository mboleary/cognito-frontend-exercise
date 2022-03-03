<template>
    <fieldset class="flex-layout vertical ">
        <label> {{text}} </label>
        <label class="option" v-for="answer of answers" v-bind:key="answer" :checked="selectedItem === answer"><input type="radio" name="type" :value="answer" v-on:change="handleChange">{{answer}}</label>
    </fieldset>
</template>

<script>
export default {
    data () {
        return {
            selectedItem: ""
        }
    },
    props: {
        text: String,
        answers: Array
    },
    methods: {
        handleChange (e) {
            if (e.target.checked) {
                this.selectedItem = e.target.value;
                this.$emit("answer", {value: this.selectedItem});
            }
        }
    }
}
</script>