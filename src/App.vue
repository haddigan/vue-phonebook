<template>
  <div id="app">
    <div class="contact-container">
      <contacts-list v-bind:contacts="contacts"></contacts-list>
      <add-contact v-on:add-contact="addContact"></add-contact>
    </div>
  </div>
</template>

<script>
import AddContact from "./components/AddContact.vue";
import ContactsList from "./components/ContactsList.vue";

export default {
  name: "App",
  components: {
    ContactsList,
    AddContact,
  },
  data() {
    return {
      contacts: [
        {
          name: "Dan",
          number: "123-4567",
        },
      ],
    };
  },
  methods: {
    addContact(contact) {
      this.contacts.push(contact);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.contact-container {
  width: 33%;
  margin: auto;
}
</style>
