<template>
  <title-page 
    v-if="page === 'title'"
    title="Quiz Demonstration Application" 
    description="You are about to take a short quiz. A summary will be shown at the end. Click the button below to start."
    v-on:start="handleStart"
  ></title-page>
  <step-view
    v-else-if="page === 'questions'"
    :questions="internalQuestions"
    v-on:finish="handleShowSummary"
  ></step-view>
  <summary-page
    v-else-if="page === 'summary'"
    :questions="internalQuestions"
    v-on:restart="handleRestart"
  ></summary-page>
</template>

<script>
import TitlePage from "./components/TitlePage.vue";
import StepView from "./components/StepView.vue";
import SummaryPage from "./components/SummaryPage.vue";
export default {
  components: { TitlePage, StepView, SummaryPage },
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
  computed: {
    internalQuestions () {
      // Don't pollute the source with additional information
      const toRet = JSON.parse(JSON.stringify(this.questions));

      for (let i = 0; i < toRet.length; i++) {
        toRet.id = i;
      }

      return toRet;
    }
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
      for (const q of this.internalQuestions) {
        delete q.response;
      }
    }
  }
};
</script>
