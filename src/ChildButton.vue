<template>
    <button @click="$emit('tombolDiklik')">Klik Saya</button>
</template>

<script>
export default {
    emits: ['TombolDiklik']
};
</script>