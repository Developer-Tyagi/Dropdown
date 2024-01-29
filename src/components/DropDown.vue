<template>
    <div>
        <div id="app" class="flex items-center justify-center bg-gray-200 min-h-screen">
            <div class="relative text-lg w-48">
                <button
                    class="flex items-center justify-between px-3 py-2 bg-white w-full border border-gray-500 rounded-lg"
                    @click="isOptionsOpen = !isOptionsOpen" @blur="isOptionsOpen = false">
                    <span>{{ selectedOption }}</span>
                    <svg fill="none" viewBox="0 0 24 24" stroke="currentColor"
                        class="h-4 w-4 transform transition-transform duration-200 ease-in-out"
                        :class="isOptionsOpen ? 'rotate-180' : 'rotate-0'">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                    </svg>
                </button>
                <transition enter-active-class="transform transition duration-900 ease-custom"
                    enter-class="-translate-y-1/2 scale-y-0 opacity-0"
                    enter-to-class="translate-y-0 scale-y-100 opacity-100"
                    leave-active-class="transform transition duration-300 ease-custom"
                    leave-class="translate-y-0 scale-y-100 opacity-100"
                    leave-to-class="-translate-y-1/2 scale-y-0 opacity-0">
                    <ul v-show="isOptionsOpen"
                        class="absolute left-0 right-0 mb-4 bg-white divide-y rounded-lg shadow-lg overflow-hidden">
                        <li v-for="(option, index) in dropdownOptions" :key="index"
                            class="px-3 py-2 transition-colors duration-300 hover:bg-gray-100"
                            @mousedown.prevent="setOption(option)">
                            {{ option.value }}
                        </li>
                    </ul>
                </transition>
            </div>
        </div>
    </div>
</template>
  
<script>
import { ref } from 'vue';

export default {
    props: {
    dropdownOptions: {
      type: Array,
      required: true
    }
  },
    setup(props) {
        console.log(props.dropdownOptions, 41);
        var isOptionsOpen = ref(false);
        var selectedOption = ref("Please select");
        const setOption = (option) => {
            selectedOption.value = option.value;
            isOptionsOpen.value = false;
        }

        return {
            isOptionsOpen,
            selectedOption,
            setOption
        };
    },
};
</script>