<template>
    <div class="form-control w-full max-w-xs text-l">
        <label class="text-l mb-2">
            <p>{{ label }}</p>
        </label>
        <select class="select w-full max-w-xs text-gray-600" required @change="updateInput">
            <option v-for="item in items" :key="item" :value="item">{{ item }}</option>
        </select>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'DropdownField',
    props: {
        label: String,
        placeholder: String,
        items: Array<string>,
        selected: String,
    },
    methods: {
        updateInput(event: any) {
            console.log('TOM', event.target.value);
            this.$emit('update:modelValue', event.target.value);
        },
    },
});
</script>

<style scoped>
select:required:invalid {
    color: hsl(204, 17.86%, 89.02%);
}
option[value=''][disabled] {
    display: none;
}
option {
    color: black;
}
</style>
