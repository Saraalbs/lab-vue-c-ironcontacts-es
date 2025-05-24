<template>
  <div class="container">
    <h1>IronContacts</h1>
    <ContactControls
      :disable-add="contacts.length === contactList.length"
      @add-random="addRandomContact"
      @sort-name="sortByName"
      @sort-popularity="sortByPopularity"
    />
    <ContactTable :contacts="contacts" @delete="deleteContact" />
  </div>
</template>
<script setup>
import { ref } from "vue";
import contactList from "./contacts.json";
import ContactControls from "./components/ContactControls.vue";
import ContactTable from "./components/ContactTable.vue";

const contacts = ref(contactList.slice(0, 5));

function addRandomContact() {
  const remaining = contactList.filter(
    (c) => !contacts.value.some((contact) => contact.id === c.id)
  );

  if (remaining.length === 0) return;

  const randomIndex = Math.floor(Math.random() * remaining.length);
  contacts.value.push(remaining[randomIndex]);
}

function sortByName() {
  contacts.value = [...contacts.value].sort((a, b) =>
    a.name.localeCompare(b.name)
  );
}

function sortByPopularity() {
  contacts.value = [...contacts.value].sort(
    (a, b) => b.popularity - a.popularity
  );
}

function deleteContact(id) {
  contacts.value = contacts.value.filter((contact) => contact.id !== id);
}
</script>

<style>
.container {
  max-width: 600px;
  margin: auto;
  font-family: sans-serif;
  text-align: center;
}

.profile-img {
  width: 50px;
  height: 70px;
  object-fit: cover;
  border-radius: 4px;
}

.sort-button,
.add-button,
.delete-button {
  margin: 5px;
  padding: 8px 12px;
  font-weight: bold;
  border: none;
  border-radius: 4px;
  color: white;
  cursor: pointer;
}

.add-button,
.sort-button {
  background-color: #3498db;
}

.add-button:disabled {
  background-color: #bdc3c7;
  cursor: not-allowed;
}

.delete-button {
  background-color: #e74c3c;
}
</style>
