<template>
    <div class="banner">
        <div class="container">
            <question-item
                :text="currText"
                :answers="currAnswers"
                v-on:answer="handleAnswer"
            ></question-item>
        </div>
        <div class="banner-footer bg-blur bg-darken ">
            <div class="container flex-layout horizontal statusbar">
                <div class="margin-top-bottom-auto flex fg-dark-color">
                    Question {{step + 1}} of {{questions.length}}
                </div>
                <div :hidden="!allowNext">
                    <button 
                        class="primary accent-1" 
                        v-on:click="finish" 
                        v-if="step >= questions.length - 1"
                    >Finish</button>
                    <button 
                        class="secondary" 
                        v-on:click="increment" 
                        v-else
                    >Next</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import QuestionItem from "./QuestionItem.vue";
export default {
    components: {QuestionItem},
    data () {
        return {
            step: 0,
            allowNext: false
        }
    },
    computed: {
        currText () {
            if (this.step >= this.questions.length) {
                return "";
            }
            return this.questions[this.step].text;
        },
        currAnswers () {
            if (this.step >= this.questions.length) {
                return [];
            }
            return this.questions[this.step].answers;
        },
    },
    props: {
        questions: {
            type: Array,
            required: true
        }
    },
    methods: {
        increment () {
            this.step += 1;
            this.allowNext = false;
        },
        finish () {
            this.$emit("finish");
        },
        handleAnswer (e) {
            this.allowNext = true;
            this.questions[this.step].response = e.value;
        }
    }
}
</script>

<style scoped>
    /** Fix bug where status text jumps when the button appears */
    .statusbar {
        height: 39px;
    }
</style>