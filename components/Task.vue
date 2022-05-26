<template>
  <div :class="`taskDiv  ${isSelected ? 'taskDivSelected' : ''}`">
    <div class="taskSelect">
      <input
        type="checkbox"
        class="taskSelectBox"
        value="`${task.id}`"
        @click="toggleSelect"
      />
    </div>
    <div class="taskContent" :title="task.content">{{ task.content }}</div>
    <div class="taskButtons">
      <img
        @click="removeTask"
        class="taskDelete"
        src="../assets/icon/trash.svg"
      />
    </div>
  </div>
</template>


<script>
export default {
  name: "Task",
  props: ["task"],
  data() {
    return {
      isSelected: false,
    };
  },
  methods: {
    removeTask() {
      this.$store.commit("TOGGLE_LOADING");
      setTimeout(() => {
        this.$store.commit("REMOVE_TASK", this.task);
        this.newTask = "";
        this.$store.commit("TOGGLE_LOADING");
      }, 1000);
    },
    toggleSelect() {
      this.isSelected = !this.isSelected;
    },
  },
};
</script>

<style>
.taskDiv {
  display: flex;
  align-items: center;
  height: 3rem;
}

.taskDiv:hover {
  background: #f8f8f8;
}
.taskDivSelected {
  color: #8dc8ff;
}

.taskFinish {
  background: green;
}

.taskUndo {
  background: gray;
}

.taskContent {
  font-size: 1.5rem;
  flex-grow: 1;
  height: 100%;
  line-height: 3rem;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
  padding-left: 1rem;
}

.taskSelect {
  display: flex;
  align-items: center;
  justify-content: center;
  padding-left: 3rem;
}

.taskSelectBox {
  margin-right: 5px;
  cursor: pointer;
  font-size: 14px;
  width: 15px;
  height: 12px;
  position: relative;
}

.taskSelectBox:after {
  position: absolute;
  width: 10px;
  height: 15px;
  top: 0;
  content: " ";
  background-color: #fff;
  color: #8dc8ff;
  border: solid 1px #c7c3c6;
  display: inline-block;
  visibility: visible;
  padding: 0px 3px;
  border-radius: 3px;
}

.taskSelectBox:checked:after {
  content: "✓";
  font-size: 12px;
  background-color: #fff;
  color: #8dc8ff;
  border: solid 1px #8dc8ff;
}

.taskButtons {
  padding-right: 3rem;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  width: 8rem;
}

.taskCheck {
  height: 1.5rem;
}

.taskDelete {
  height: 2rem;
  cursor: pointer;
}
</style>