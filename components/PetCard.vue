<script setup lang="ts">
  defineProps({
    id: {
      type: Number,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    breed: {
      type: String,
      required: true,
    },
    sex: {
      type: String,
      required: true,
    },
    dateOfBirth: {
      type: String,
      required: true,
    },
    imageUrl: {
      type: String,
      required: true,
    },
  })
</script>
<template>
  <div class="w-full md:w-6/12 lg:w-4/12 xl:w-3/12">
    <div
      class="m-3 pg-on-surface-container-text pg-surface-container px-6 py-12 rounded-3xl shadow-xl text-center"
    >
      <img
        :src="imageUrl"
        class="mb-4 mx-auto rounded-xl w-full sm:w-9/12"
        alt="..."
        width="600"
        height="600"
      />
      <h5 class="font-bold mb-2">
        {{ name }}
      </h5>
      <p class="mb-6 pg-secondary-text text-sm">
        {{ breed }}
      </p>
      <BaseButton size="lg" :to="`/adopt/${id}`">
        <span>Adopt Now</span>
        <Icon
          name="ri:heart-add-fill"
          size="24"
          class="text-tertiary-600 md:ml-1.5"
        ></Icon>
      </BaseButton>
    </div>
  </div>
</template>
<style scoped></style>
