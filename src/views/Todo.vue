<template>
    <div>
      <h1>TODO List</h1>
      <input type="text" class="input" v-model="todoText" placeholder="Task...">
      <div class="buttons">
        <button class="btn" @click="addTask" :disabled="!todoText">Add task</button>
        <button class="btn" @click="deleteAll">Delete All</button>
      </div>
      <div class="list" v-for="(item, key) in items" :key="key">
        <span class="item">{{ 'Task ' + (key + 1) }}:  {{ item.text }}</span>
        <button class="btn red" @click="deleteElem(key)">Delete</button>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Todo',
  data () {
    return {
      todoText: '',
      items: []
    }
  },
  methods: {
    addTask () {
      this.items.push({ text: this.todoText })
      this.todoText = ''
    },
    deleteAll () {
      this.items = []
    },
    deleteElem (key) {
      this.items.splice(key, 1)
    }
  }
}
</script>

<style scoped>
.input {
  height: 30px;
  font-size: 20px;
  border-style: none;
  box-shadow: 0 0 10px 8px #2c3e50;
}
.buttons {
  margin-top: 20px;
  display: flex;
  justify-content: center;
}
.btn {
  margin: 5px;
  box-shadow: inset 0 0 0 0 #ffffff;
  background: linear-gradient(to bottom, #f9f9f9 5%, #e9e9e9 100%);
  background-color: #f9f9f9;
  border-radius: 5px;
  border: 1px solid #dcdcdc;
  display: inline-block;
  cursor: pointer;
  color: #666666;
  font-family: Arial;
  font-size: 15px;
  font-weight: bold;
  padding: 7px 24px;
  text-decoration: none;
  text-shadow: 0 0 0 #ffffff;
}
.btn:hover {
  background: linear-gradient(to bottom, #e9e9e9 5%, #f9f9f9 100%);
  background-color: #e9e9e9;
}
.list {
  display: flex;
  justify-content: center;
}
.item {
  font-size: 20px;
  margin: 12px;
  width: 200px;
  text-overflow: ellipsis;
  border: 3px solid gray;
  box-shadow: 0 2px 10px 1px gray;
  border-radius: 5px;
}
.red {
  margin: 10px;
}
</style>
