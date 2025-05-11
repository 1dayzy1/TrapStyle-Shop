<template>


    


    <div class="flex items-center mt-6 flex-wrap ">

        <section class="section">

            <div class="border-1 rounded-xl border-slate-200 ml-20 w-60 hover:shadow-2xl transition hover:-translate-1  ">
                

                <!-- <div class="block-slider"> -->

                    <!-- <button @click="prevSlide()" class="button-slide prevSlide">
                        <i class="fas fa-chevron-left"></i>
                    </button> -->

                    

                    <!-- <button @click="nextSlide()" class="button-slide nextSlide">
                        <i class="fas fa-chevron-right"></i>
                    </button> -->


                <!-- </div> -->


                <img :src="it.imageUrl" class="w-50 ml-6 ">
                
                <p class="text-center">{{it.title }}</p>
                
                <p class="text-center font-bold mt-4">Цена:{{ it.price }} рублей</p>

                <p v-if="productQuant" class="text-center text-lg    font-bold">У вас в корзине:{{ productQuant }}</p>


                <div class="flex justify-center">
                    <!-- <button @click="opendata()">Показать данные</button> --> 
                    <button class="w-40 h-10 bg-orange-400 rounded-md mb-6 mt-4 cursor-pointer hover:bg-orange-500 transition"  @click="AddToBasket()">Добавить в коризну</button>
                    <!-- <button class="button-open"  @click="OpenModal()">Доп.информация</button> -->

                </div>

                


            </div>

        </section>

    </div>



</template>



<script>
import { ref } from 'vue';




export default{
    name:"CardBlock",
    props:['it'],

    computed:{
        productQuant(){
            return this.$store.getters.productQuantity(this.it);
        }
    },

    methods:{

        

        AddToBasket(){
            this.$store.state.shownotification = true;
            this.$store.commit('AddToBasket',this.it)

            // console.log(this.it);
            

            setTimeout(() => {
                this.$store.state.shownotification = false;
                
            }, 3000);
        },

        OpenModal(){
            this.$store.commit('OpenModal',this.it)
        },



    },

    setup(){
        const indexImage = ref([
            {image:'img-home1.png'},
            {image:'img-home2.png'},
            {image:'img-home3.png'},
            {image:'img-home4.png'},
            {image:'img-home5.png'},
            
        ]);


        const index = ref(0);

        const prevSlide = () => {
            index.value = (index.value - 1 + indexImage.value.length) % indexImage.value.length;
        }

        const nextSlide = () => {
            index.value = (index.value + 1) % indexImage.value.length;
        }

        return{
            indexImage,
            index,
            prevSlide,
            nextSlide
        }

    }



}

</script>



