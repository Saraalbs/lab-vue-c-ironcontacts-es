<template>
  <tr>
    <td>
      <img :src="contact.pictureUrl" alt="picture" class="profile-img" />
    </td>
    <td>{{ contact.name }}</td>
    <td>{{ contact.popularity.toFixed(2) }}</td>
    <td>{{ contact.wonOscar ? "🏆" : "" }}</td>
    <td>{{ contact.wonEmmy ? "🏆" : "" }}</td>
    <td>
      <button
        @click="$emit('delete', contact.id)"
        class="delete-button"
        :aria-label="`Delete ${contact.name}`"
      >
        Delete
      </button>
    </td>
  </tr>
</template>

<script setup>
defineProps({
  contact: Object,
});
defineEmits(["delete"]);
</script>
