<template>


<div class="fixed w-full h-full top-0 left-0 bg-black z-10 opacity-70" >

</div>

<div class="bg-white  w-96  h-full fixed right-0 top-0 z-20 p-8 flex flex-col">

  <div class="flex items-center gap-5">

    <svg xmlns="http://www.w3.org/2000/svg" @click="closeDrawer" width="20" height="20" fill="currentColor" class="rotate-180 cursor-pointer opacity-50 transition hover:opacity-100 hover:-translate-1" viewBox="0 0 16 16">
      <path fill-rule="evenodd"
        d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8" />
    </svg>

    <h2 class="text-2xl font-bold ">Корзина</h2>

    
    


  </div>

  <div class="overflow-y-auto flex-grow">
      <div class="card" v-for="it in draw" :key="it.id">
        <img :src="it.imageUrl" class="img-home" alt="Изображение товара" />
        <p class="name-home">{{ it.title }}</p>
        <p class="price-home">{{ it.price }}</p> <!--  Отображаем отформатированную цену -->

        <!-- Блок управления количеством -->
        <div class="flex items-center justify-between mt-2">
          <div  class="w-4 h-4 bg-blue-500 rounded-md flex items-center justify-center cursor-pointer" @click="DeleteToDrawer(it)" >-</div>
          <span>{{ it.quantity }}</span> <!-- Отображение количества -->
          <div  class="w-4 h-4 bg-blue-500 rounded-md flex items-center justify-center cursor-pointer" @click="AddToDrawer(it)">+</div>
        </div>
      </div>

    
    
    

  </div>
        
       

  <div class="border-t py-4">



    <b>Сумма: {{ sum }}$</b>

    
    <div class=" w-50 h-10 flex justify-around items-center cursor-pointer  bg-lime-300  rounded-md mt-6 hover:bg-lime-400 transition ">Оформить заказ <svg xmlns="http://www.w3.org/2000/svg"  width="20" height="20" fill="currentColor" class="" viewBox="0 0 16 16">
      <path fill-rule="evenodd"
        d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8" />
    </svg></div>

    

  </div>

  

</div>

</template>




<script>





export default{
    name:"DrawerBlock",
    components:{
      
    },

   

    props:['draw', 'sum'],

    methods:{
      closeDrawer(){
        
        this.$store.state.openDrawer = false;
      },

      AddToDrawer(it){
        it.quantity++;
        this.$store.state.totalSum+= it.price;
      },

      DeleteToDrawer(it){
        if(it.quantity > 1){
          this.$store.state.totalSum-= it.price
          it.quantity--;
        }
        else{
          this.$store.state.totalSum-= it.price;
          this.$store.state.basket = this.$store.state.basket.filter( i=> i.id !== it.id);
        }
      }

      
    },

        
    

  }


</script>



<style scoped>


.img-home{
  width: 90px;
  height: 80px;
  margin: 0 auto;
}

</style>