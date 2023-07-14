<template>
    <div> 
        <div class="row">
            <div class="form-group">
                <label for="">Name</label>
                <input type="text" v-model="configForm.champName">
            </div>
            <div class="form-group">
                <label for="">Type</label>
                <input type="text" v-model="configForm.champType">
            </div>
            <div class="form-group">
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault" v-model="configForm.champObligatoire">
                    <label class="form-check-label"  for="flexCheckDefault">
                        Champs oblogatoire
                    </label>
                </div>
                
            </div>

            <div class="form-group">
                    <label for="">Déscription</label>
                   
                    <textarea name="" id="" class="form-control"  v-model="configForm.description"></textarea>
            </div>
           

            <div class="form-group">
                <button @click="validerChamps">Valider</button>
            </div>
        </div>
        
    </div>
</template>

<script>
export default {
    props:["existingValue"],
    data() { 
        return {
             configForm: {
                champName: this.existingValue?.champName,
                champObligatoire: this.existingValue?.champObligatoire,
                description: this.existingValue?.description,
            },
        }
    },
    methods: {
        validerChamps() {
            this.$emit("validerChamps", this.configForm);
        }
    }
}
</script>

<style lang="scss" scoped>

</style>