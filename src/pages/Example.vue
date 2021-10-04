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
import { defineComponent, onMounted, reactive, toRefs } from 'vue';
import ExampleComponent from 'components/ExampleComponent.vue';

export default defineComponent({
  name: 'PageExample',
  components: { ExampleComponent },
  setup() {
    const state = reactive({
      meta: { totalCount: 1200 },
      todos: [
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
        }
      ]
    });

    onMounted(() => {
      console.log('mounted!');
    });

    return { ...toRefs(state) };
  }
});
</script>
