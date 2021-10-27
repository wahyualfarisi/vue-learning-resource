<template>
  <base-dialog v-if="inputInValid" title="Invalid Value" @close="confirmError">
    <template #default>
        <p>Something went wrong</p>
        <p>Please Check your Input</p>
    </template>
    <template #actions>
        <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitHandler">
        <div class="form-control">
          <label for="title">Title</label>
          <input type="text" name="title" id="title" ref="title" />
        </div>
         <div class="form-control">
          <label for="description">description</label>
          <textarea type="text" name="description" id="description" rows="3" ref="description" />
        </div>
        <div class="form-control">
          <label for="link">Link</label>
          <textarea type="url" name="link" id="link" ref="link" />
        </div>
        <base-button type="button">Add Resource</base-button>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue'
export default {
  data(){
    return {
      inputInValid: false
    }
  },
  components: { BaseButton },
  inject: ['addResource'],
  methods: {
    submitHandler(){
        const title = this.$refs.title.value;
        const description = this.$refs.description.value;
        const link = this.$refs.link.value;

        if(
          title.trim() === '' ||
          description.title() === '' ||
          link.trim() === ''
        ) {
          this.inputInValid = true
          return;
        }

        let data = {
          title,
          description,
          link
        }
        this.addResource(data);
    },
    confirmError(){
      this.inputInValid = false
    }
  }
}
</script>

<style scoped>
  label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
  }

  input,
  textarea {
    display: block;
    width: 100%;
    font: inherit;
    padding: 0.15rem;
    border: 1px solid #ccc;
  }

  input:focus,
  textarea:focus {
    outline: none;
    border-color: #3a0061;
    background-color: #f7ebff;
  }

  .form-control {
    margin: 1rem 0;
  }
</style>