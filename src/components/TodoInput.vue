<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" />
    <!-- <button v-on:click="addTodo">add</button> -->
    <span class="addContainer" v-on:click="addTodo">
      <i class="fas fa-plus addBtn" aria-hidden="true"></i>
    </span>
  </div>
</template>
<script>
import "@fortawesome/fontawesome-free/css/all.css";

export default {
  data: function () {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    addTodo: function () {
      if (this.newTodoItem !== "") {
        var obj = { completed: false, item: this.newTodoItem };        
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        this.clearInput();
      }
    },
    clearInput: function () {
      this.newTodoItem = "";
    },
  },
};
</script>

<style scoped>
.inputBox {
  background: back;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  display: flex;
  align-items: center;
  padding: 0 10px;
  text-align: center;
}

.inputBox input {
  text-align: center;
  border-style: none;
  font-size: 0.9rem;
  flex: 1;
  height: 100%;
}

.addContainer {
  background: linear-gradient(to right, #62eac6, #32cee6);
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.addBtn {
  color: white;
}
</style>
