<template>
  <v-card>
      <v-flex xs12 sm10>
        <v-tree url="/item/category/list/"
                :isEdit="isEdit"
                @handleAdd="handleAdd"
                @handleEdit="handleEdit"
                @handleDelete="handleDelete"
                @handleClick="handleClick"
        />
      </v-flex>
  </v-card>
</template>

<script>
  export default {
    name: "category",
    data() {
      return {
        isEdit:true
      }
    },
    methods: {
      handleAdd(node) {
        this.loading=true;
        this.$http.post("/item/category", node)
        this.loading = false;
      },
      handleEdit(id, name) {
        this.loading=true;
        this.$http.put("/item/category", {id,name})
        this.loading = false;
      },
      handleDelete(id) {
        this.loading=true;
        this.$http.delete("/item/category/"+id)
        this.loading = false;
      },
      handleClick(node) {
        console.log(node)
      }
    }
  };
</script>

<style scoped>

</style>
