<script>
import axios from 'axios'
import "bootstrap/dist/css/bootstrap.min.css"
export default {
    data() {
        return {
            message: "hello doggie",
            img: String,
            breed: String
        }
    },
    props: ["numb"],
    methods: {
        getPic() {
            axios(" https://dog.ceo/api/breeds/image/random")
                .then(res => {
                    console.log(res.data)
                    this.img = res.data.message
                    this.getBreed(res.data.message)
                })
        },
        getBreed(thePath) {
            let aryDog = thePath.split("/")
            console.log(aryDog);
            this.breed = aryDog[4].toUpperCase()
        }
    },
    mounted() {
        this.getPic();
    }
}
</script>


<template>
    <div class="card" style="width: 18rem;">

        <img v-bind:src=img class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">{{ numb }} {{ breed }}</h5>

            <a v-on:click=getPic href="#" class="btn btn-primary">Get Another Dog</a>
        </div>
    </div>
</template>

<style scoped>
h5 {
    color: red
}
img{
    height:300px
}
</style>