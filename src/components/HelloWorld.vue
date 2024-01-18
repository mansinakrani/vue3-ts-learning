<script setup lang="ts">
defineProps<{
  msg: string
}>()

// 1. Props with Types
// NO need to import defineProps or withDefaults as it's macro
//(i)
// defineProps<{ msg: string }>()

//(ii)
// const props = defineProps<{ msg: string }>() // can use as {{msg}} or {{props.msg}}

//(iii)Only works with experimental turned on for vue 3.3 - loose reactivity, if not required => ?:
// const { msg= 'hello' } = defineProps<{ msg?: string }>()

//(iv) Can't combine
// defineProps<{ msg: string }>({ msg: String })

//(v)Generic Types Script Setup
//<script setup lang='ts' generic='T extends string'>
// import { type GenericComp } from './types'
//defineProps<GenericComp<T>>()

//---------------------------------------

// 2. Show Props prop types Object (defineComponent)
// import type { PropType } from 'vue'

// export interface Props {
//   msg: string
// }

// defineProps({
//   msg: Object as PropType<Props>
// })

//---------------------------------------
// 3. Import types from external files - vue 3.3

// import type { GenericCompTypes } from './types'

// defineProps<GenericCompTypes>()

// interface Props {
//   Book: GenericCompTypes
// }

//---------------------------------------
// 4. Show withDefaults
// const props = withDefaults(defineProps<{ msg?: string }>(), { msg: 'hello'})

//---------------------------------------
// 5. Show types with define Emits Types
// const emit = defineEmits<{
//   (e: 'change', id: number): void
//   (e: 'update', value: string): void
// }>()

//new style

// const emit = defineEmits<{
//   change: [id: number]
//   update: [value: string]
// }>()

//---------------------------------------
// 6. Show Types with Ref/Reactive/Computed

// import { ref, type Ref } from 'vue'
// const year: Ref<string | number> = ref(2020)

// const year = ref<number>() // number | undefined
// const year = ref<number>({} as known as number)

// import { reactive } from 'vue';
// const book = reactive({ title: 'Vue 3' })

import { computed, ref } from 'vue'
const count = ref(0)
// const double = computed(() => count.value * 2)
//generic
const double = computed<number>(() => {
  // type error if this doesn't return a number
  return 10
})

//---------------------------------------
// 7. Event Handlers

function handleChange(event: Event) {
  console.log((event.target as HTMLInputElement).value)
}

function handleKeyPress(event: KeyboardEvent) {
  console.log((event.target as HTMLInputElement).value)
}

</script>

<template>
  <div class="greetings">
    <h2>Typescript basics</h2>
    <div>Message : {{ msg }}</div>
    <!-- <div>{{ props.msg }}</div> -->
    <!-- <div>{{ year }}</div> -->
    <input @keypress="handleKeyPress"/>
    <!-- <h1 class="green">{{ msg }}</h1> -->
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
