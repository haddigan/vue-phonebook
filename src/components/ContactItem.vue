<template>
  <div class="contact-item">
    <div class="contact-item-icon">{{ contact.name.substr(0, 1) }}</div>
    <div class="contact-item-data">
      <p class="contact-item-data-name">{{ contact.name }}</p>
      <p class="contact-item-data-number">{{ contact.number }}</p>
    </div>
    <div class="contact-item-control">
      <button
        class="contact-item-control-button"
        v-on:click="deleteContact(contact)"
      >
        ❌
      </button>
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  props: ["contact"],
  methods: {
    deleteContact(contact) {
      this.$emit("delete-contact", contact);
    },
  },
};
</script>
<style scoped>
.contact-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 1em 0.5em;
}
.contact-item + .contact-item {
  border-top: 1px solid lightgray;
}
.contact-item:nth-child(even) {
  background-color: ghostwhite;
}
.contact-item:hover {
  background-color: aliceblue;
}
.contact-item-data {
  display: flex;
  flex: 1;
  flex-direction: column;
  align-items: flex-start;
}
.contact-item-data-name,
.contact-item-data-number {
  margin: 0;
  padding: 0;
}
.contact-item-data-name {
  font-weight: 700;
}
.contact-item-data-number {
  font-size: 0.9em;
}
.contact-item-icon {
  margin-right: 2em;
  width: 3em;
  height: 3em;
  line-height: 3em;
  border-radius: 50px;
  background-color: darkslategray;
  color: white;
  font-weight: 900;
}
.contact-item-control-button {
  border: 0;
  background: transparent;
  font-size: 1.5em;
  cursor: pointer;
}
</style>
