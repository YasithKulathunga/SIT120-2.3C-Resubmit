<template>
    <div>
        <!--06. List Rendering-->
        <div class="break">
          <span style="font-weight: 600;font-size: 30px;">List Rendering</span><br>
          <!--06.A - List rendering : v-for with an object -->
          <p>v-for with an object</p>
          <ul class="left">
            <li v-for="(value, key, index) in myMovie"> {{ index }}. {{ key }}: {{ value }}</li>
          </ul>
        </div>
        <div class="break1">
          <!--06.B - List rendering : v-for with an Range -->
          <p>v-for with an Range</p>
          <span v-for="n in 10">{{ n }}</span>
        </div>
        <div class="break1">
          <!--06.C - List rendering : v-for on template -->
          <p>v-for on template</p>
          <template v-for="movie in movies" : key="movie">
            <h1 class="green">{{ movie }}</h1>
            <hr/>
          </template>
        </div>
        <div class="break1">
          <!--06.D -List rendering : v-for with v-if -->
          <h3>v-for with v-if</h3>
            <li v-for="item in products">
              {{ item.name }}
              <span v-if="item.price >= 1000">(Expensive)</span>
              <span v-else>(Cheap)</span>
            </li>
        </div>
        <div class="break1">
             <!--06.E -List rendering : v-for with a component -->
            <todo/>
        </div>
    </div>
</template>

<script>
import todo from "./components/todo.vue"

export default{
    components: {
    todo,
    },

    data(){
        return {
            /*06.A */
        myMovie: {
          name: 'ready player one',
          director: 'Steven Spielberg',
          year: 2019,
          rating: 8.5,
          genre: 'Action',
        },
        /*06.C */
        movies: ['Avatar', 'Avengers: Endgame', 'Avengers: Endgame 2'],
        /*06.D */
        products: [
          { name: 'Macbook', price: 1300 },
          { name: 'Iphone', price: 990 },
          { name: 'Monitor', price: 350 },
        ],
        name: '',
        }
    }
}
</script>

<style>
    .break{
  margin-top: 50px;

}

.break1{
  margin-top: 10px;

}
</style>