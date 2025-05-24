<template>
  <table>
    <thead>
      <tr>
        <th>Picture</th>
        <th>Name</th>
        <th>Popularity</th>
        <th>Won Oscar</th>
        <th>Won Emmy</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      <ContactRow
        v-for="contact in contacts"
        :key="contact.id"
        :contact="contact"
        @delete="emit('delete', $event)"
      />
      <tr v-if="contacts.length === 0">
        <td colspan="6">No contacts to display.</td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import ContactRow from "./ContactRow.vue";

const props = defineProps({
  contacts: Array,
});
const emit = defineEmits(["delete"]);
</script>
