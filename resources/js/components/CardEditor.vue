<template>
  <div>
    <textarea
        ref="card"
        :value="value"
        class="rounded-md shadow-card py-1 px-2 outline-none w-full text-gray-900 text-sm bg-white h-16 resize-none"
        placeholder="Enter a title for this card..."
        @keyup.esc="closed"
        @keyup.enter="saved"
        @input="$emit('input', $event.target.value)"
    ></textarea>

    <div class="flex">
      <button
          class="rounded-sm py-1 px-3 bg-indigo-700 text-white cursor-pointer hover:bg-indigo-600 outline-none"
          @click="saved"
      >{{ label }}
      </button>
      <button
          class="py-1 px-3 ml-1 rounded-md hover:bg-gray-400 cursor-pointer text-gray-500"
          @click="closed"
      >Cancel
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardEditor",
  props: ['value', 'label'],
  mounted() {
    this.$refs.card.focus();
  },
  methods: {
    closed() {
      this.$emit('closed');
    },
    saved() {
      this.$emit("saved");
    }
  }
}
</script>

<style scoped>

</style>