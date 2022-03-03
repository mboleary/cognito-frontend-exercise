<template>
  <title-page 
    v-if="page === 'title'"
    title="Quiz Demonstration Application" 
    description="You are about to take a short quiz. A summary will be shown at the end. Click the button below to start."
    v-on:start="handleStart"
  ></title-page>
  <step-view
    v-else-if="page === 'questions'"
    :questions="questions"
  ></step-view>
</template>

<script>
import TitlePage from "./components/TitlePage.vue";
import StepView from "./components/StepView.vue";
export default {
  components: { TitlePage, StepView },
  props: {
    questions: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      page: "title"
    };
  },
  methods: {
    handleStart () {
      this.page = "questions";
    },
    handleShowSummary () {
      this.page = "summary";
    },
    handleRestart () {
      this.page = "title";
    }
  }
};
</script>
