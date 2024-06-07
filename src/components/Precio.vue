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
        <div type="button" class="btn btn-white border">
            S/. {{ vprecio }} <span class="badge text-bg-dark ms-2">4</span>
        </div>
    </div>
</template>
<style lang="scss" scoped></style>