<script setup lang="ts">
import { toRefs } from 'vue';
import { type WorkoutType, type Workouts } from '../type/WorkoutMockTypes';
import DialogImage from "./DialogImage.vue"

const props = defineProps<{
  selectedWorkout: keyof WorkoutType,
  workouts: Workouts[]
}>()
const { workouts } = toRefs(props);
</script>


<template>
    <div class="box-card">
      <div v-for="exercise in workouts" :key="exercise.workout" class="box-container" >
        <p class="text pink">{{ exercise.workout }}</p>
        <span class="description item">{{ exercise.description }}</span>
        <DialogImage :workoutName="exercise.workout" :image="exercise?.image"/>
      </div>
    </div>
</template>

<style>
.box-card {
  padding: 16px;
  width: 100%;
}

.box-container {
  margin-top: 16px;
}

.text {
  font-weight: 500;
  padding-right: 16px;
}

.description {
  font-weight: 300; 
  font-size: 16px;
  color: #303133;
}
</style>