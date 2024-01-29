<template>
  <DropDown :dropdownOptions="dropdownOptions" />
</template>

<script>
import { defineComponent, ref } from 'vue'
import DropDown from './components/DropDown.vue'

export default defineComponent({
  components: {
    DropDown
  },
  setup() {
    const dropdownOptions = ref([
      { key: 1, value: 'One' },
      { key: 2, value: 'Two' },
      { key: 3, value: 'Three' },
      { key: 4, value: 'Four' },
      { key: 5, value: 'Five' },
    ]);

    return {
      dropdownOptions,
    };
  }
})
</script>
