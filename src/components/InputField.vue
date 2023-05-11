<template>
    <div class="form-control w-full max-w-xs text-l">
        <label class="text-l mb-2">
            <p>{{ label }}</p>
        </label>
        <input type="text" :placeholder="placeholder" class="input input-bordered w-full max-w-xs text-gray-600" :value="modelValue" @input="updateInput" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'InputField',
    props: {
        label: String,
        placeholder: String,
        modelValue: String,
    },
    methods: {
        updateInput(event: any) {
            this.$emit('update:modelValue', event.target.value);
        },
    },
});
</script>

<style scoped>
::placeholder {
    /* Chrome, Firefox, Opera, Safari 10.1+ */
    color: hsl(200.57, 17.95%, 80%);
    opacity: 1; /* Firefox */
}

:-ms-input-placeholder {
    /* Internet Explorer 10-11 */
    color: hsl(200.57, 17.95%, 80%);
}

::-ms-input-placeholder {
    /* Microsoft Edge */
    color: hsl(200.57, 17.95%, 80%);
}
</style>
