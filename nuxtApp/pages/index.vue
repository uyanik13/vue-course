<template>
  <div class="container">
    <div
      class="h-100 w-full flex items-center justify-center bg-teal-lightest font-sans"
    >
      <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
        <div class="mb-4">
          <h1 class="text-grey-darkest">Todo List</h1>
          <div class="flex mt-4">
            <input
              v-model="title"
              class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker"
              placeholder="Add Todo"
            />
            <button
              @click="addTodo"
              class="flex-no-shrink bg-red-500 text-white rounded-lg p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal"
            >
              Add
            </button>
          </div>
        </div>
        <div>
          <div
            class="flex mb-4 items-center"
            v-for="item in todoList"
            :key="item.id"
          >
            <p class="w-full text-grey-darkest">
              {{ item.title }}
            </p>
            <button
              @click="removeTodo(item.id)"
              class="flex-no-shrink bg-indigo-500 text-white rounded-lg p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red"
            >
              Remove
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    todoList() {
      return this.$store.getters["todo/todoList"];
    },
  },
  data() {
    return {
      title: "Todo ",
    };
  },
  methods: {
    addTodo() {
      let tempData = {
        id: this.todoList.length + 1,
        title: this.title,
      };
      return this.$store.dispatch("todo/addTodo", tempData);
    },
    removeTodo(id) {
      return this.$store.dispatch("todo/removeTodo", id);
    },
  },
  created() {
    this.$store.dispatch("todo/getTodoList");
  },
};
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
