<template>
    <div>
       <div class="container-fluid">
        <div class="row">
            <div class="col-2">
                <LeftSide/>
            </div>
            <div class="col-8">
                <board id="bord-1">
                    <card
                    id="card-1"
                    :draggable="true"
                    >
                    <h1>ello </h1>
                    </card>
                </board>
                <board id="bord-2">
                    <card
                    id="card-2"
                    :draggable="true"
                    >
                    <h1>Card 3 </h1>
                    </card>
                </board>
            </div>
            <div class="col-2"></div>
        </div>
        
       </div>
    </div>
</template>

<script>
import LeftSide from '@/components/side/LeftSide.vue'
import Board from '@/components/bord/Board.vue'
import Card from '@/components/bord/Card.vue'
    export default {
  components: { LeftSide, Board, Card },
        
    }
</script>

<style lang="scss" scoped>

</style>