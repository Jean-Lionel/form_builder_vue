<template>
    <div 
    >
        
    </div>
</template>

<script>
export default {
    props: ["id"],
    methods: {
        drop: e => {
            console.log(e)
            const card_id = e.datatransfer.getData('card_id');
            const card = document.getElementById(card_id);
            card.style.display = 'block';
            e.target.appedChild(card);
        }
    }
        
    }
</script>

<style lang="scss" scoped>

</style>