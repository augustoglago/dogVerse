<template>
<q-page class="container flex column flex-center justify-around">
    <q-img class="image" :src="imageUrl" />
    <h4 class="title q-ma-sm text-center">"{{ itens.text }}"</h4>
    <h5 class="title q-ma-sm text-center">{{ itens.book }} {{ itens.chapter }}: {{ itens.number }}</h5>
    <q-btn class="button" unelevated rounded label="Gerar Versículo" @click="init(), randomImage()" />
</q-page>
</template>

<script>
import {
    defineComponent,
    ref,
    onMounted
} from 'vue'
//import axios from 'axios'
// import {
//     createClient
// } from 'pexels';

export default defineComponent({
    name: 'PhraseOfDay',
    setup() {
        const itens = ref([])
        const imageUrl = ref([])
        const bookName = ref()
        const init = async () => {
            try {
                const response = await fetch('https://www.abibliadigital.com.br/api/verses/nvi/random')
                const data = await response.json()
                itens.value = data
                bookName = itens.book.name
                console.log(itens)

            } catch (error) {
                console.log(error)
            }
        };

        const randomImage = async () => {
            const responseDog = await fetch('https://dog.ceo/api/breeds/image/random')
            const dataDog = await responseDog.json()
            imageUrl.value = dataDog.message
            return imageUrl
        };

        // const searchPhoto = async () => {
        //     try {
        //         const response = await fetch('https://api.pexels.com/v1/search/?page=1&per_page=1&query=cat', {
        //             headers: {
        //                 Authorization: apiKey,
        //             }
        //         })
        //         const data = await response.json();
        //         photos.value = data.photos.src
        //         console.log(photos.value)

        //     } catch (error) {
        //         console.log(error)
        //     }
        // };

        // const createPost = async () => {
        //     try {
        //         const response = await axios.get('https://www.abibliadigital.com.br/api/users/:augustoglago@gmail.com', {
        //             headers: {
        //               Authorization: "Augusto eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IkZyaSBTZXAgMDEgMjAyMyAxOTozNToyNCBHTVQrMDAwMC5hdWd1c3RvY2hvY29ib0BnbWFpbC5jb20iLCJpYXQiOjE2OTM1OTY5MjR9.QQ26E1BX-ip5e-5ARAHkbFoKSTETmGUfMn9ErJTzc4w"
        //             },
        //         })
        //         console.log(response.data)

        //     } catch (error) {
        //         if (error.response) {
        //             console.error('Erro de resposta da API:', error.response.data);
        //         } else {
        //             console.error('Erro ao fazer a solicitação:', error.message);
        //         }

        //     }
        // };

        onMounted(async () => {
            //reatePost(),
            init()
            randomImage()
        });

        return {
            init,
            itens,
            randomImage,
            imageUrl,
        }
    }
}, )
</script>

<style>
.container {
    background-color: #f95179;
}

.title {
    color: #fff;
}

.button {
    width: 20%;
    height: 50px;
    background-color: #262525;
    color: white;
    margin-bottom: 20px;
}

.image {
    width: 40%;
    height: 100%;
}
</style>
