<template>
  <div class="todo">
    <center><h1>To-do List</h1></center>
    <div>
      <input type="text" v-model="newItem" placeholder="Add new item" />
      <button @click="addItem" :disabled="newItem.length === 0">Add</button>
    </div>

    <div>
      <ul class="list">
        <li
          class="list-item"
          v-for="(item, i) in items"
          :key="i"
          :class="{ completed: item.completed }"
        >
          <span @click="toggleComplete(item)">{{ item.name }}</span>
          <input v-model="item.name" v-if="!item.isHidden" />
          <button @click="item.isHidden = !item.isHidden">Edit / Done</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: "",
      items: [
        { id: 1, name: "Clean the Fridge", completed: false, isHidden: true },
        { id: 2, name: "Walk the dogs", completed: false, isHidden: true },
      ],
    };
  },
  methods: {
    addItem() {
      this.items.push({
        id: this.items.length + 1,
        name: this.newItem,
        completed: false,
        isHidden: true,
      });
      this.newItem = "";
    },
    toggleComplete(item) {
      item.completed = !item.completed;
    },
    editItem() {
      this.items.name = this.items.name.toUpperCase();
      return this.items.name;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.todo {
  margin: 0 30%;
  padding: 18px 6px;
  background-color: lightblue;
}
button {
  background-color: #4caf50;
  color: orange;
  width: 20%;
  padding: 15px;
  margin: 10px 0px;
  border: none;
  cursor: pointer;
  border-radius: 7px;
  font-size: 14px;
  font-weight: bold;
}

input[type="text"] {
  width: 70%;
  margin: 8px 20px;
  padding: 12px 20px;
  border: 2px solid green;
  box-sizing: border-box;
  border-radius: 7px;
}
button:hover {
  opacity: 0.7;
}

.list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.list-item {
  padding: 0 16px;
  border: 1px solid #e8e8e8;
  // cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 6px;
  border-radius: 4px;
}

.list-item span {
  color: white;
  font-weight: 300;
  cursor: pointer;
}

.list-item input {
  padding: 12px 20px;
  border: 2px solid green;
  box-sizing: border-box;
  border-radius: 7px;
  outline: none;
}

.list-item.completed {
  border: 1px solid #4fc08d;
}

.list-item.completed span {
  text-decoration: line-through;
  color: green;
}
</style>
