<template>
  <title-page title="Quiz Demonstration Application" description="You are about to take a short quiz. A summary will be shown at the end. Click the button below to start."></title-page>
</template>

<script>
import TitlePage from './components/TitlePage.vue';
export default {
  components: { TitlePage },
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
  }
};
</script>
