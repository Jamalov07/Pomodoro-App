<template>
  <button class="py-[19px] px-[28px] rounded-full">
    {{ textContent }}
  </button>
</template>
<script>
export default {
  name: "Button",
  props: {
    textContent: String,
  },
};
</script>
<style></style>
