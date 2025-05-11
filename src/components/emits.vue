<template>
    <ChildButton @tombolDiklik="tanganiKlik" />
</template>

<script>
import ChildButton from './ChildButton.vue';

export default {
    components: { ChildButton },
    methods: {
        tanganiKlik() {
            alert('Pesan dari anak diterima');
        }
    }
}
</script>