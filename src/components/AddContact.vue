<template>
  <div class="add-contact">
    <button
      class="add-contact-control-button"
      v-on:click="openForm"
      v-show="!isCreating"
    >
      Add Contact
    </button>
    <div class="add-contact-form" v-show="isCreating">
      <div class="add-contact-form-control">
        <label>Name</label>
        <input
          class="add-contact-form-control-input"
          v-model="contactName"
          type="text"
          ref="contactName"
          defaultValue=""
        />
      </div>
      <div class="add-contact-form-control">
        <label>Phone Number</label>
        <input
          class="add-contact-form-control-input"
          v-model="number"
          type="text"
          ref="number"
          defaultValue=""
        />
      </div>
      <div class="add-contact-form-actions">
        <button
          class="add-contact-form-add-button"
          v-on:click="submitContact()"
        >
          Create
        </button>
        <button class="add-contact-form-cancel-button" v-on:click="closeForm">
          Cancel
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contactName: "",
      number: "",
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    submitContact() {
      if (this.contactName.length > 0 && this.number.length > 0) {
        this.$emit("add-contact", {
          name: this.contactName,
          number: this.number,
          id: Date.now(),
        });
        this.contactName = "";
        this.number = "";
        this.isCreating = false;
      }
    },
  },
};
</script>
<style scoped>
.add-contact {
  margin: 1em 0;
}
.add-contact-form {
  display: flex;
  flex-direction: column;
  border: 1px solid lightgray;
  border-radius: 2px;
  padding: 1em 0.5em;
}
.add-contact-form-control {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  flex-grow: 1;
}
.add-contact-form-control-input {
  width: 98%;
  height: 2em;
  line-height: 1em;
}
.add-contact-form-actions {
  display: flex;
  flex: 1 0 auto;
  justify-content: end;
  margin: 1em 0 0;
}
.add-contact-control-button,
.add-contact-form-add-button,
.add-contact-form-cancel-button {
  color: white;
  background-color: darkslategray;
  border: 0;
  cursor: pointer;
  padding: 0.8em;
  font-size: 1em;
  font-weight: 700;
  border-radius: 2px;
}
.add-contact-control-button {
  width: 100%;
}
.add-contact-form-cancel-button {
  color: darkslategray;
  border: 0;
  background: transparent;
}
</style>
