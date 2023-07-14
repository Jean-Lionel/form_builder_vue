<template>
    <div>
        <div class="row">
        <div class="col">
            <button @click="createAsimpleText">
                Simple text
            </button>
        </div>
        <div class="col">
          Column
        </div>
    </div>
    </div>
</template>

<script>
    export default {
    methods: {
            createAsimpleText() {
            this.$emit('createAsimpleText');
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>