<template>
  <div class="contacts-list">
    <div class="no-contacts-message" v-show="contacts.length <= 0">
      Click Add Contact to get started
    </div>
    <contact-item
      v-for="contact in contacts"
      v-bind:contact="contact"
      v-bind:key="contact.id"
      v-on:delete-contact="deleteContact"
    ></contact-item>
  </div>
</template>
<script type="text/javascript">
import ContactItem from "./ContactItem.vue";

export default {
  components: { ContactItem },
  props: ["contacts"],
  methods: {
    deleteContact(contact) {
      const contactIndex = this.contacts.indexOf(contact);
      this.contacts.splice(contactIndex, 1);
    },
  },
};
</script>
<style>
.contacts-list {
  border: 1px solid lightgray;
  border-radius: 2px;
}
.no-contacts-message {
  padding: 1em;
  font-style: italic;
  color: darkgray;
}
</style>
