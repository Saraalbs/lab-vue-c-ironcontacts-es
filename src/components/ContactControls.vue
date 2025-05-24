<template>
  <div>
    <button
      @click="$emit('add-random')"
      class="add-button"
      :disabled="disableAdd"
    >
      Add Random Contact
    </button>
    <button @click="$emit('sort-name')" class="sort-button">
      Sort by Name
    </button>
    <button @click="$emit('sort-popularity')" class="sort-button">
      Sort by Popularity
    </button>
  </div>
</template>

<script setup>
defineProps({
  disableAdd: Boolean,
});
defineEmits(["add-random", "sort-name", "sort-popularity"]);
</script>
