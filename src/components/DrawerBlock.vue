<template>

<form action="https://api.web3forms.com/submit" method="POST">

  <input type="hidden" name="access_key" value="41dd4a81-1d8c-47f0-95ad-59a1f7845804">
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

<div v-if="this.$store.state.basket.length === 0" >

    

  <div class="flex justify-center items-center mt-70">
    <img src="/img/draw.svg" alt="" >
  </div>
  <p class="text-center text-2xl font-bold">Корзина пустая</p>
  <p class="text-center mt-2 font-normal">Добавьте хотя бы одну пару <br> кроссовок, чтобы сделать заказ.</p>
  <div class="flex items-center justify-center mt-6 w-3xs h-12 bg-lime-300 cursor-pointer  rounded-md ml-8 hover:bg-lime-400 transition" @click="closeDrawer"> <svg xmlns="http://www.w3.org/2000/svg"  width="20" height="20" fill="currentColor" class="rotate-180 mr-4 " viewBox="0 0 16 16">
      <path fill-rule="evenodd"
        d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8" />
    </svg>Вернуться назад</div>
  
 

</div>


  <div  class="overflow-y-auto flex-grow ">


    
      <div  class="card " v-for="it in draw" :key="it.id" >
        
        <img :src="it.imageUrl" class="img-home" alt="Изображение товара"   />
        <input class="" type="text"  :placeholder="it.title" :value="it.title" name="Товар" required >
        <input class="name-home" type="text" :placeholder="it.price" :value="it.price"  >
        

        <!-- Блок управления количеством -->
        <div class="flex items-center justify-between mt-2">
          <div  class="w-4 h-4 bg-blue-500 rounded-md flex items-center justify-center cursor-pointer" @click="DeleteToDrawer(it)" >-</div>
          <input class="" type="text"  :placeholder="it.quantity" :value="it.quantity" name="Количество" required >
          <div  class="w-4 h-4 bg-blue-500 rounded-md flex items-center justify-center cursor-pointer" @click="AddToDrawer(it)">+</div>
        </div>
      </div>

      
    
    
    

  </div>
        
       

  <div class="border-t py-4" v-if="this.$store.state.basket.length >= 1">


    <label for="check-phone" class="text-xl font-bold">Введите номер телефона или аккаунт телеграмм для связи</label>
    <input type="text" name="Номер телефона" placeholder="+ 7 999 000 22-43" class="border rounded-md mt-4 mb-4"  id="check-phone"   required ><br>

    <span>Сумма: </span>
    <input class="name-home" type="number" :placeholder="sum" :value="sum" name="Общая сумма" required  >
    <b>Рублей</b>
    
    <button type="submit" class="w-50 h-10 flex justify-around items-center cursor-pointer  bg-lime-300  rounded-md mt-6 hover:bg-lime-400 transition ">Оформить заказ <svg xmlns="http://www.w3.org/2000/svg"  width="20" height="20" fill="currentColor" class="" viewBox="0 0 16 16">
      <path fill-rule="evenodd"
        d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8" />
    </svg></button>
    

    

    

  </div>
 

  

</div>

</form>

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
        this.$store.state.counter++
        this.$store.state.totalSum+= it.price;
      },

      DeleteToDrawer(it){
        if(it.quantity > 1){

          this.$store.state.totalSum-= it.price
          it.quantity--;
          this.$store.state.counter--;
        }
        else{
          this.$store.state.counter--;
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