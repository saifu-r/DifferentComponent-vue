<template>
  <base-dialog v-if="inputIsInvalid" @close="confirmError" title="Invalid Input">
  <template #default>
    <p>Unfortunately, at least one input value is invalid</p>
    <p>Please check all the inputs</p>
  </template>

  <template #actions>
    <base-button @click="confirmError">Okay</base-button>
  </template>
</base-dialog>
  <base-card>
    <form @submit.prevent="submitWebsite">
      <div class="form-control">
        <label>Title</label>
        <input id="title" name="title" type="text" v-model="enteredTitle" />
      </div>
      <div class="form-control">
        <label>Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          v-model="enteredDescription"
        ></textarea>
      </div>
      <div class="form-control">
        <label>Link</label>
        <input id="link" name="link" type="url" v-model="enteredLink" />
      </div>
      <div>
        <base-button type="submit">Add Website</base-button>
      </div>
    </form>
  </base-card>
</template>

<script lang="ts">
import { ref, inject } from "vue";

export default {
  setup() {
    const enteredTitle = ref("");
    const enteredDescription = ref("");
    const enteredLink = ref("");
    const inputIsInvalid = ref(false);

    const addWebsite = inject("addwebsite");

    const submitWebsite = () => {
      if (
        enteredTitle.value.trim() === "" ||
        enteredDescription.value.trim() === "" ||
        enteredLink.value.trim() === ""
      ) {
        // alert("please input data")
        inputIsInvalid.value = true;
      } else {
        addWebsite(
          enteredTitle.value,
          enteredDescription.value,
          enteredLink.value
        );
        enteredTitle.value = "";
        enteredDescription.value = "";
        enteredLink.value = "";
      }
    };

    const confirmError= ()=>{
        inputIsInvalid.value = false;
    }

    return {
      enteredTitle,
      enteredDescription,
      enteredLink,
      submitWebsite,
      inputIsInvalid,
      confirmError
    };
  },
};
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