<template class="">
  <v-container>
    <v-card class="card" color="white">
      <v-card-title>
        <p class="tag" height="10px" :style="`background: ${todo.color}`">
          {{ todo.name }}
        </p>
      </v-card-title>

      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-wrap description">{{
            todo.description
          }}</v-list-item-title>
          <!-- <v-icon small left color="black"> {{ todo.tag }} </v-icon> -->
        </v-list-item-content>
      </v-list-item>
    </v-card>
  </v-container>
</template>
<script>
export default {
  props: {
    todo: {
      type: Object,
      default: () => ({}),
      required: false,
    },
  },
};
</script>
<style scoped>
.card {
}
.tag {
  color: white;
  font-weight: bold;
  font-size: 13px;
  margin-bottom: -15px;
  line-height: 110%;
  padding: 1px 7px;
  border-radius: 4px;
}
span {
  color: white;
}
.description {
  font-size: 14px;
  margin-bottom: -5px;
}
</style>
