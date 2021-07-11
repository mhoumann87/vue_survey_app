<template>
  <learning-survey @survey-submit="storedSurvey"></learning-survey>
  <user-experience> :results="savedSurveyResults"></user-experience>
</template>

<script>
  import LearningSurvey from './components/survey/LearnningSurvey.vue';
  import UserExperience from './components/survey/UserExperience.vue';

  export default {
    components: {
      LearningSurvey,
      UserExperience,
    },
    data() {
      return {
        savedSurveyResults: [],
      };
    },
    methods: {
      storedSurvey(surveyData) {
        const surveyResult = {
          name: surveyData.userName,
          rating: surveyData.rating,
          id: new Date().toISOString(),
        };

        this.savedSurveyResults.push(surveyResult);
        console.log(surveyResult);
      },
    },
  };
</script>

<style>
  *,
  ::before,
  ::after {
    box-sizing: border-box;
  }

  html {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  body {
    margin: 0;
  }
</style>
