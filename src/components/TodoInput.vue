<template>
  <div class="inputBox">
    <input type="text" v-model="newTodoItem" placeholder="Type what you have to do"
        v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fas fa-plus" area-hidden="true"></i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ''
    }
  },
  methods: {
    addTodo() {
      // console.log(this.newTodoItem);

      // 입력 텍스트가 널값이 아닐 경우만 저장
      if (this.newTodoItem != "") {
        localStorage.setItem(this.newTodoItem, this.newTodoItem);   // 로컬 스토리지에 저장(키,값)
        this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = '';
    }
  }
}
</script>

<style>
  input:focus {
    outline: none;
  }
  .inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
  }
  .inputBox input{
    border-style: none;
    font-size: 0.9rem;
  }
  .addContainer {
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
  }
  .addBtn {
    color: white;
    vertical-align: middle;
  }
</style>
