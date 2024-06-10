<script setup>
const props = defineProps({
    vprecio: {
        type: String,
        required: true,
    }
})
</script>
<template>
    <div>

        S/. {{ vprecio }}

    </div>
</template>
<style lang="scss" scoped></style>