<template>
    
</template>

<script>
import Summary from "./Summary.vue";

export default {
    data: () => ({
        currPage: "title",
        
    }),
    props: {
        text: String,
        answers: Array
    }
}
</script>