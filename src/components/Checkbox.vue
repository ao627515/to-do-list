<template>
  <input
    type="checkbox"
    v-model="task.completed"
    class="form-checkbox h-5 w-5"
    @change="onChange"
  />
  <span :class="{ completed: task.completed }" class="flex-1">{{
    task.title
  }}</span>
</template>

<script setup>
defineProps({
  task: Object,
});

const emits = defineEmits(["check", "uncheck"]);

const onChange = (e) => {
  // console.log(e);

  if (e.currentTarget.checked) {
    emits("check", e.currentTarget);
  } else {
    emits("uncheck", e.currentTarget);
  }
};
</script>
