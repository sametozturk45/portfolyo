<template>
    <div>
        <div class="position-relative overflow-hidden">
            <v-carousel height="50rem" cycle continuous hide-delimiters hide-delimiter-background>
                <v-carousel-item
                v-for="item in 5"
                :key="item"
                src="https://picsum.photos/1920"
                eager
                ></v-carousel-item>
            </v-carousel>
        </div>
        <div class="pa-4 pb-14">
            <v-card>
                <v-card-title>Lorem İpsum</v-card-title>
                <v-card-text>
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Quas aut perferendis adipisci, atque debitis sed obcaecati quisquam vero earum deleniti voluptatum consequuntur. Officia, laborum est fugiat fuga consequuntur eius nobis.
                    Exercitationem illo, ex minus nostrum repellendus est deleniti repudiandae natus tenetur velit, enim magni veritatis magnam, totam ea laudantium consectetur eaque dolor corporis quam dicta doloremque ratione. Veniam, inventore ratione?
                    Deserunt fuga porro soluta libero, tempore praesentium odio harum aliquam atque voluptatibus maxime veniam quod quos voluptas officia, modi beatae ut molestiae illo? Vel quo nam neque nostrum nesciunt eum.
                    Iusto quo laudantium illum ad doloribus asperiores quam, et hic corrupti, delectus non molestias porro eligendi necessitatibus nisi fuga nam architecto, distinctio magni ut magnam eos ipsum harum ipsa! Est!
                    Nihil unde libero dolores adipisci saepe excepturi dolorum soluta incidunt, veritatis ab deserunt ullam, ea esse aliquam eum culpa optio error amet hic voluptatum recusandae voluptatem! Suscipit architecto repudiandae exercitationem.
                    Modi sint corrupti excepturi aspernatur minima itaque suscipit assumenda, repellat asperiores nulla nobis autem expedita distinctio! Excepturi repellendus iure quibusdam eaque a laborum distinctio, ab atque adipisci reiciendis qui tempora!
                    Consectetur, magni nisi beatae aperiam, officia totam tenetur pariatur ad sint consequatur sit perferendis velit recusandae illum repellat? Debitis sed iste deserunt rerum culpa quidem incidunt esse totam dolorum est.
                    Numquam veniam vel asperiores nihil dolore quis ut dolorum. Corrupti, labore. Repellendus excepturi aperiam, illo amet architecto ullam totam enim ducimus tempore natus esse quam eius provident incidunt officia possimus?
                    Quidem placeat praesentium, sunt deserunt necessitatibus enim at, voluptatem alias tenetur vitae laudantium possimus hic porro eligendi soluta ipsam animi. Inventore repellendus harum dolorem amet suscipit expedita temporibus aut dolores.
                    Reiciendis, corrupti! Minus mollitia est nesciunt hic, optio natus. Neque magnam odit suscipit eos soluta repudiandae assumenda maiores ducimus? Eum porro molestias obcaecati blanditiis reprehenderit aut error quasi laboriosam in.
                </v-card-text>
            </v-card>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ProjeDetay',
        head(){
            return{
                title:'Lorem İpsum'
            }
        },
        created() {
            this.$nuxt.$emit('transparent-appbar', true)
            this.$nuxt.$emit('fixed-appbar', true)
        },
    }
</script>