<template>
  <section>
    <base-card>
      <h2>How was your learning experience?</h2>
      <form @submit.prevent="submitSurvey">
        <div class="form-control">
          <label for="name">Your Name</label>
          <input type="text" name="name" id="name" v-model.trim="enteredName" />
        </div>

        <h3>My learning experience was....</h3>
        <div class="form-control">
          <input
            type="radio"
            name="rating"
            id="rating-poor"
            value="poor"
            v-model="chosenRating"
          />
          <label for="rating-poor">Poor</label>
        </div>

        <div class="form-control">
          <input
            type="radio"
            name="rating"
            id="rating-average"
            value="average"
            v-model="chosenRating"
          />
          <label for="rating-average">Average</label>
        </div>

        <div class="form-control">
          <input
            type="radio"
            name="rating"
            id="rating-great"
            value="great"
            v-model="chosenRating"
          />
          <label for="rating-poor">Great</label>
        </div>

        <p v-if="invalidInput">
          One or more input fields are invalid. Please check your provided data.
        </p>

        <div>
          <base-button>Submit</base-button>
        </div>
      </form>
    </base-card>
  </section>
</template>

<script>
  export default {
    emits: ['survey-submit'],
    data() {
      return {
        enteredName: '',
        chosenRating: null,
        invalidInput: false,
      };
    },
    methods: {
      submitSurvey() {
        if (this.enteredName === '' || !this.chosenRating) {
          this.invalidInput = true;
          return;
        }

        this.invalidInput = false;
        this.$emit('survey-submit', {
          userName: this.enteredName,
          rating: this.chosenRating,
        });
      },
    },
  };
</script>

<style scoped>
  .form-control {
    margin: 0.5rem 0;
  }

  label {
    font-weight: bold;
  }

  input[type='text'] {
    display: block;
    width: 20rem;
    margin-top: 0.5rem;
    padding: 0.5rem;
  }
</style>
