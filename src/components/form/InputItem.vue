<template>
    <div>
        <div class="form-group row mb-2"  >
            <div class="col-4"><label for="" class="form-label">{{ item.name }}
                <span v-if="item.required">*</span>
            </label></div>
            <div class="col-6 input-group">
               
                <div v-if="isEditing" class="text-white bg-success">
                    Editing ...
                </div>
                <input type="text" name="" id="" class="form-control form-control-sm" placeholder="" aria-describedby="helpId">
                <button>
                    <small style="cursor:pointer;" id="helpId" class="text-muted" @click="chooseDetail(index, item)">
                        <i class="bi bi-pen"></i></small>
                    </button>
                </div>
            </div>
            
        </div>
    </template>
    
    <script>
    export default {
        props: ["item", "isEditing", "index"],
        methods: {
                chooseDetail(index, item) {
                this.$emit("chooseDetail", {
                    index,
                    item
                })
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>