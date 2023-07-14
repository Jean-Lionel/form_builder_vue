<template>
    <div class="form-group">
        <label for="">{{ item.name }}</label>

        <div class="input-group">
            <div v-if="isEditing" class="text-white bg-success">
                        Editing ...
                </div>
        <select class="form-control form-control-sm">
                <option v-for="el in item.items" :value="el.value">{{ el.option }}</option>
            </select>
            <button>
                        <small style="cursor:pointer;" id="helpId" class="text-muted" @click="chooseDetail(index, item)">
                            <i class="bi bi-pen"></i></small>
                        </button>
        </div>
        
    </div>
</template>

<script>
    export default {
    props: ["item", "index","isEditing"],

    methods: {
        chooseDetail(index, item) {
            this.$emit("chooseSelectDetail", {
                item: item,
                index: index
            })
        }
    }
    }
</script>

<style lang="scss" scoped>

</style>