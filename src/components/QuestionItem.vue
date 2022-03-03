<template>
    <fieldset class="flex-layout vertical ">
        <label> {{text}} </label>
        <label class="option" v-for="answer of answers" v-bind:key="answer"><input type="radio" name="type" :value="answer">{{answer}}</label>
    </fieldset>
</template>

<script>
export default {
    data: () => ({
        selectedItem: ""
        
    }),
    props: {
        text: String,
        answers: Array
    }
}
</script>