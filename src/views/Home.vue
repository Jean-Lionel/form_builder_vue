<template>
    <div>
        <div class="container-fluid">
            <div class="row">
                <div class="col-2">
                    <LeftSide 
                    @createAsimpleText="createAsimpleText"
                    @createSelectType="createSelectType"
                    />
                </div>
                <div class="col-8">
                    <div v-for="(item,i) in inputList">
                        <input-item v-if="item.type == 'text'"
                        :isEditing="i == choosedIndex"
                        :item="item"
                        :index="i"
                        @chooseDetail="chooseDetail"
                        />
                       <select-form 
                       v-if="item.type == 'select'" 
                       :isEditing="i == choosedIndex"
                       :item="item"
                       :index="i"
                       @chooseSelectDetail="chooseSelectDetail"

                       @addOption="addOption"
                       /> 
                    </div>
                    <div>
                        <button @click="generateSaveForm">Generate A form</button>
                    </div>
                </div>
                <div class="col-2">

                    <!-- v-if="displayForm == 'SELECT'" -->

                    <select-fome-detail 
                    @addOption="addOption"
                    
                    />                    
                    <input-form v-if="displayForm == 'INPUT_TEXT'" :existingValue="existingValue" @validerChamps="validerChamps"/>
                    
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
import LeftSide from '@/components/side/LeftSide.vue'
import Board from '@/components/bord/Board.vue'
import Card from '@/components/bord/Card.vue'
import InputForm from '@/components/form/InputForm.vue'
import InputItem from '@/components/form/InputItem.vue'
import SelectForm from '@/components/form/SelectForm.vue'
import SelectFomeDetail from '@/components/form/SelectFomeDetail.vue'
export default {
    components: { LeftSide, Board, Card, InputForm, InputItem, SelectForm, SelectFomeDetail },
    data() { 
        return {
            existingValue: {},
            inputList: [
            
            ],
            choosedIndex: -1,

            displayForm : "",
        }
    },
    
    methods: {
        addOption(item) {
            this.inputList[this.choosedIndex].items = item;
        },
        chooseSelectDetail(item) { 
             this.choosedIndex = item.index;
            this.existingValue = item.item;
            this.displayForm = "SELECT";
        },
        generateSaveForm() { 
            console.log(this.inputList)
        },
        createSelectType() { 
            const item = {
                name: "Select Item",
                required: false,
                description: "",
                label: "Select Item",
                type: 'select',
                items: [],
            }
            this.inputList.push(item);
    
        },
        createAsimpleText() {
            
            this.inputList.push({
                name : "Simple Text",
                type : "text",
                type : "text",
            });
        }, 
        validerChamps(e) {
            this.inputList[this.choosedIndex] = {
                name: e.champName,
                required: e.champObligatoire,
                description: e.description,
                label: e.champName,
                type: 'text',
            };
            console.log(e)
        },
        chooseDetail(item) {
            this.choosedIndex = item.index;
            this.existingValue = item.item;
             this.displayForm = "INPUT_TEXT";
        }
    }
    
}
</script>

<style lang="scss" scoped>

</style>