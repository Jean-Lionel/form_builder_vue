<template>
    <div>
        <div class="row">
            
            <div class="col-12">
                <ol>
                    <li v-for="(item, i ) in optiontionList" class="d-flex justify-content-between">
                       
                        <span> {{ item }}</span>
                        <span @click="removeItem(i)" style="cursor:pointer">X</span>
                    </li>
                </ol>
            </div>
            <div class="col-12">
                <div class="input-group mb-3">
                    <input type="text" class="form-control form-control-sm" 
                    v-model="optionValue"
                    placeholder="Nouvel option" aria-label="Recipient's username" aria-describedby="basic-addon2">
                    <span style="cursor:pointer;" class="input-group-text" id="basic-addon2" title="Ajouter" @click="addOption">
                        <i class="bi bi-node-plus-fill"></i>
                    </span>
                </div>
            </div>

            <div class="col-12">
                <button @click="saveValidate">Sauvegarder</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:["existingValue"],
    data() {
        return {
            optionValue: "",
            optiontionList: [],
            required : false,
        }
    },
    mounted() { 
       this.optiontionList = [];
    },
    watch: {
        existingValue(e) {  
            this.optiontionList = this.existingValue?.item?.items?.items ?? [];
        }
    },
    methods: {
        removeItem(index) {
             this.optiontionList.splice(index, 1);
        },
        saveValidate() {
            this.$emit("addOption", {
                items: this.optiontionList,
                required : this.required
            } );
         },
        addOption() {
            if (this.optionValue.trim().length > 2) {
              
               this.optiontionList.push(this.optionValue);
                this.optionValue = "";
            } else {
                alert("Entre une nouvel valeur");
            }
        }
    }
}
</script>

<style lang="sass" scoped>

</style>