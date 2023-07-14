<template>
    <div>
        <div class="container-fluid">
            <div class="row">
                <div class="col-2">
                    <LeftSide @createAsimpleText="createAsimpleText"/>
                </div>
                <div class="col-8">
                    <div v-for="(item,i) in inputList">
                        <div class="form-group row mb-2"  >
                            
                            <div class="col-4"><label for="" class="form-label">{{ item.champName }}
                                <span v-if="item.champObligatoire">*</span>
                            </label></div>
                            <div class="col-8 input-group">
                                <div v-if="choosedIndex == i" class="text-white bg-success">
                                   Editing ...
                                </div>
                                <input type="text" name="" id="" class="form-control form-control-sm" placeholder="" aria-describedby="helpId">
                                <button>
                                    <small style="cursor:pointer;" id="helpId" class="text-muted" @click="chooseDetail(i, item)">
                                        <i class="bi bi-pen"></i></small>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-2">
                        <input-form :existingValue="existingValue" @validerChamps="validerChamps"/>
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
    export default {
        components: { LeftSide, Board, Card, InputForm },
        data() { 
            return {
                existingValue: {},
                inputList: [
                
                ],
                choosedIndex : -1,
            }
        },
        
        methods: {
            createAsimpleText() {
                this.inputList.push({
                    name : "Simple Text",
                });
            }, 
            validerChamps(e) {
                this.inputList[this.choosedIndex] = {
                    champName: e.champName,
                    champObligatoire: e.champObligatoire,
                    description: e.description,
                };
            },
            chooseDetail(index, item) {
                this.choosedIndex = index;
                this.existingValue = item;
            }
        }
        
    }
</script>

<style lang="scss" scoped>

</style>