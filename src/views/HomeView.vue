<script setup lang="ts">
import { reactive, ref, toRefs } from 'vue';
import {Job} from '@/types/Job'
// import TheWelcome from '../components/TheWelcome.vue'
// const name = ref('John');

// const age = ref<number | string>(24); // generic argument for assigning types

// return { name, age },

// const state = reactive({
//   name: 'John',
//   age: 25 as string | number // type assertive used to assign var types
// })

// return { ...toRefs(state) }

// methods: {
//     changeName(name: string) {
//       this.name = name
//       return name
//     },
//     changeAge(age: number | string) {
//       this.age = age
//       return age
//     }
//   }

const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
    ])
    return { jobs }

</script>

<template>
  <main>
    <!-- <TheWelcome /> -->
    <h3>HOME</h3>
    <p>{{ name }} - {{ age }}</p>
    <!-- <button @click="changeName('Zack')">change name</button>
    <button @click="changeAge('30')">change age</button> -->
  </main>
</template>
