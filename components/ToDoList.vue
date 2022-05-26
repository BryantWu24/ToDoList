<template>
  <div class="todoDiv">
    <div class="todoTitle"><h1>Todo List</h1></div>
    <div class="todoTask">
      <Task v-for="task in $store.state.tasks" :key="task.id" :task="task" />
    </div>
    <div class="todoEditor">
      <input
        class="todoInput"
        type="text"
        v-model="newTask"
        v-on:keyup.enter="$event.target.blur()"
        placeholder="請輸入要做的事情"
        @keypress.enter="addTask"
      />
      <div @click="addTask" class="todoSendBtn">
        <img src="../assets/icon/plus.svg" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {
    Task: () => import("./Task"),
  },
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.$store.commit("TOGGLE_LOADING");
        setTimeout(() => {
          this.$store.commit("ADD_TASK", this.newTask);
          this.newTask = "";
          this.$store.commit("TOGGLE_LOADING");
        }, 1000);
      }
    },
  },
};
</script>

<style>
.todoDiv {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 4px;
  border: solid 1px #c7c3c6;
  background-color: white;
}

.todoTitle {
  padding-left: 1.5rem;
}

.todoTask {
  height: 90%;
  width: 100%;
}

.todoEditor {
  position: absolute;
  bottom: 0px;
  height: 3rem;
  width: 100%;
  display: flex;
  justify-content: space-around;
}

.todoInput {
  height: 1.5rem;
  width: 90%;
  border: solid 1px #c7c3c6;
  border-radius: 4px;
}

.todoInput::placeholder {
  color: #c7c3c6;
}

.todoSendBtn {
  background-color: #8dc8ff;
  border: none;
  height: 1.8rem;
  width: 1.8rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4px;
}

.todoSendBtn img {
  height: 1.3rem;
  width: 1.3rem;
}
</style>