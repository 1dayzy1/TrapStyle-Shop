<template>

    <div class="container-Call">

        <p class="sale">По всем вопросам</p>
        <p class="number-sale">+7 979 027-57-12</p>


    </div>
    <div class="button-header" @click="OpenModalCall()" v>Заказать звонок</div>


    <div class="basket-cart">
        <p class="">{{this.$store.state.totalSum  }}</p>
        <svg xmlns="http://www.w3.org/2000/svg" width="26" height="26" fill="currentColor" class="cursor-pointer opacity-50 hover:opacity-100 transition relative " @click="openBasket"  viewBox="0 0 16 16">
  <path d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .49.598l-1 5a.5.5 0 0 1-.465.401l-9.397.472L4.415 11H13a.5.5 0 0 1 0 1H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5M3.102 4l.84 4.479 9.144-.459L13.89 4zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4m7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4m-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2m7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2"/>
</svg>
        
    </div>
    

</template>



<script>



export default{
    name:"CallNumber",
    methods:{
        OpenModalCall(){
            this.$store.state.OpenModalCall = true;
        },

        openBasket(){
    this.$store.state.openDrawer = true;
  }
    }

}


</script>



<style scoped>





.sale{
    color: #00000073;
    font-size: 13px;
    font-weight: 700;

}

.number-sale{
    color: #000;
    font-size: 18px;
    font-weight: 500;
    margin-top: 4px;
}


.button-header{
    width: 168px;
    height: 44px;
    color: #000;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 15px;
    font-weight: 500;
    border-radius: 6px;
    margin-left:32px ;
    background-color:#FFA400 ;
    cursor: pointer;
}

</style>