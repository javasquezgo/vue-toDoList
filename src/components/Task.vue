<script setup>
import { inject } from "vue";

const task = inject("tasks");

console.log(task);
</script>
<template></template>