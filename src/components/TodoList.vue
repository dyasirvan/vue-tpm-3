<template>
  <div class="container">
    <div class="content">
      <ol>
        <li v-for="item in todoItems" :key="item">{{ item }}</li>
      </ol>
      <input type="text" v-model="todoValue" />
      <button @click="add">Tambahkan</button>
      <br />
      <span class="text-danger" v-if="isError"> {{ pesanError }}</span>
      <span>{{ pesan }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      todoItems: [],
      todoValue: "",
      message: "",
      isError: false,
      pesanError: "Tidak boleh kosong!",
    };
  },
  methods: {
    add() {
      if (this.todoValue === "") {
        this.isError = true;
        return;
      }
      this.todoItems.push(this.todoValue);
      this.todoValue = "";
    },
  },
  computed: {
    pesan() {
      return this.todoItems.length > 3 ? "Hebat!" : "";
    },
  },
};
</script>
<style scoped>
.container {
  display: flex;
  justify-content: center;
  height: 100vh;
}
.content{
  width: 30%;
  margin: 0 auto;
  text-align: center;
}
button {
  margin-left: 10px;
  background-color: #1976d2;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
}
input {
  padding: 8px;
  border: 1px solid #455a64;
  border-radius: 5px;
}
li{
  text-align: left;
}
.text-danger {
  color: #d32f2f;
}
</style>
