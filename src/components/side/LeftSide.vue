<template>
    <div>
        <div class="row">
        <div class="col">
            <button @click="createAsimpleText">
                Simple text
            </button>
        </div>
        <div class="col">
           <button @click="createSelectType">
                    Select Type
                </button>
        </div>
    </div>
    </div>
</template>

<script>
    export default {
    methods: {
            createAsimpleText() {
            this.$emit('createAsimpleText');
            },
            createSelectType() {
            this.$emit('createSelectType');
            },
        }
    }
</script>

<style lang="scss" scoped>

</style>