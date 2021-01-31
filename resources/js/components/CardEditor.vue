<template>
  <div>
    <textarea
        v-model="title"
        class="rounded-md shadow-card py-1 px-2 outline-none w-full text-gray-900 text-sm bg-white h-16 resize-none"
        placeholder="Enter a title for this card..."
        ref="card"
        @keyup.esc="$emit('closed')"
        @keyup.enter="$emit('closed')"
    ></textarea>
  </div>
</template>

<script>
export default {
  name: "CardEditor",
  data() {
    return {
      title: null
    }
  },
  mounted() {
    this.$refs.card.focus();
  }
}
</script>

<style scoped>

</style>