<template>
  <q-page class="row items-center justify-evenly">
    <example-component
      title="Example component"
      active
      :todos="todos"
      :meta="meta"
    ></example-component>
  </q-page> 
</template>

<script>
import { defineComponent, ref } from 'vue';
import ExampleComponent from 'components/ExampleComponent.vue';

export default defineComponent({
  name: 'PageExample',
  components: { ExampleComponent},
  setup() {
    const todos = ref([
      {
        id: 1,
        content: 'content 1'
      },
      {
        id: 2,
        content: 'content 2'
      },
      {
        id: 3,
        content: 'content 3'
      },
      {
        id: 4,
        content: 'content 4'
      },
      {
        id: 5,
        content: 'content 5'
      }
    ]);
    const meta = ref({
      totalCount: 1200
    });
    return { todos, meta };
  } 
});
</script>
