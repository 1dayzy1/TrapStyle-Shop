<template>

<div class="modalcall animate__animated animate__fadeInDown p-6" v-if="this.$store.state.OpenModalCall">


   


    
        <form action="https://api.web3forms.com/submit" method="POST">

       
        <input type="hidden" name="access_key" value="d45e86d2-9a71-45c8-a765-ffd70dfd2d29">

            
        <p class="username">Введите ваше имя</p>
        <input type="text" name="Имя" class="input pl-10" placeholder="Имя" required>
        <p class="user-info">Введите суть вашего вопроса</p>
        <input type="text" name="Тема" class="input pl-10" placeholder="Тема" required><br>
       
        <p class="text-3xl">Введите номер телефона</p>
        <input type="number" name="Номер телефона" class="input pl-10" required placeholder="+ 7 999 000"><br>
       
       
    

        <button type="submit" class="button d-inline w-40 h-10 bg-orange-300 rounded-md cursor-pointer mt-10 mr-10 hover:bg-orange-400 transition">Отправить</button>
        <button  class="button d-inline w-40 h-10 rounded-md cursor-pointer transition bg-gray-400 hover:bg-gray-600"  @click="CloseModal()">Закрыть</button>

        </form>


</div>

</template>



<script>


export default{
    name:"ModalCall",
    methods:{
        CloseModal(){
            this.$store.state.OpenModalCall = false;
        }
    }
}


</script>


<style scoped>

.modalcall{
    position: fixed;
    width: 30%;
    
    border-radius: 20px;
    background-color: #fff;
    
    box-shadow: 4px 15px 59px 15px rgba(34, 60, 80, 0.27);
    left: 30vw;
    top: 250px;
    
}

form{
    margin-left: 5vw;
    
}


.close-modal{
    margin-left: 30vw;
    margin-top: 1vh;
    transition: 300ms;
}

.close-modal:hover{
    color: red;
    cursor: pointer;
}


.username{
    font-size: 24px;
    font-weight: 600;
}

.input{
    width: 20vw;
    height: 5vh;
    border: 1px solid;
    margin-left: 10px;
    border-radius: 5px;
}


.user-info{
    font-size: 24px;
    font-weight: 600;
}






@media (max-width:1500px) {
    .modalcall{
        width: 55vw;
        padding: 20px;
    }

    .input{
        width: 37vw;
    }

    .button{
        margin-top: 10px;
        

    }
}

</style>