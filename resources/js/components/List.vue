<template>
  <div class="bg-gray-300 rounded-sm p-2 mr-2 list">
    <div class="flex justify-between">
      <div class="text-gray-800 pl-2 font-bold">{{ list.title }}</div>
    </div>

    <Card
        v-for="card in list.cards"
        :key="card.id"
        :card="card"
        @deleted="$emit('card-deleted', {...$event, listId: list.id})"
    ></Card>

    <CardAddEditor
        v-if="editing"
        :list="list"
        @added="$emit('card-added', {...$event, listId: list.id})"
        @closed="editing = false"
        @updated="$emit('card-updated', {...$event, listId:  list.id})"
    ></CardAddEditor>
    <CardAddButton v-else @click="editing = true"></CardAddButton>

  </div>
</template>

<script>
import Card from "./Card";
import CardAddButton from "./CardAddButton";
import CardAddEditor from "./CardAddEditor";

export default {
  name: "List",
  components: {Card, CardAddButton, CardAddEditor},
  props: {
    list: {
      type: Object
    }
  },
  data() {
    return {
      editing: false
    }
  }
}
</script>

<style scoped>
.list {
  width: 250px;
  min-width: 250px;
}
</style>