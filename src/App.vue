<template>
    <div>
      <div>
        <span class="heading">Template Syntax</span>
        <!--01. A Text Interpolation -->
        <div>
          <h1>{{ title }}</h1>
        </div>
        <div>
        <!--0.1 B Using HTML derectives to change the color of the text -->
          <p v-html="htmlElement"></p>
        </div>
        <div>
        <!--0.1 C Attribute bindings -->
          <button v-bind:disabled="isDisabled">Texting attribute binding</button>
        </div>
        <div>
          <!--0.1 D Javascript expression inside syntax -->
          {{ ok ? 'Okay' : 'Nah' }}
          {{ number + 1 }}
          {{ fname.toUpperCase() }}
        </div>
      </div>

      <div class="break">
        <!--02. Methods-->
        <span class="heading">Methods</span>
        <h2>Multiply : {{ multiply(10) }}</h2>
        <h2>Add : {{ add(150) }}</h2>
      </div>

      <div class="break">
        <!--03. Reactivity Fundamentals [ref(), <script setup>] file : reactivity.vue-->
          <reactivity/>
      </div>

      <div class="break">
        <!--04. Computed Properties file : computed.vue-->
        <span class="heading">Computed Properties</span><br>
        <computed/>
      </div>

      <div class="break">
        <span class="heading">Class and Style Bindings</span><br>
        <!--05. Class and Style Bindings-->
        <div>
          <!--05.A - Binding HTML class [v-bind:class]-->
          <h1 class="red" v-bind:class="status" >Warning!!</h1>
          <h1 class="green" v-bind:class= "emergency">Exit -></h1>
        </div>
        <div class="break1">
          <!--05.B - Binding Inline Styles [v-bind:style]-->
          <p v-bind:style="{
              'font-size' : titlesize + 'px',
              }">Using <span v-bind:style="{color : textbackground,}">inline style bind</span> in vue3 </p>
        </div>
      </div>
      <div>
        <!--06.List Rendering A,B,C,D,E file: listrendering.vue-->
        <listrendering/>
      </div>

      <div class="break">
        <!--07 Event Handling -->
        <span class="heading">Event Handling</span><br>
        <div>
          <!--07.A Event Handling : Inline Handlers -->
          <h3>Inline Handlers</h3>
          <h1>{{ newname }}</h1>
          <button class="button" v-on:click="newname ='Spiderman'">Reveal</button>

          <h2>Count</h2>
          <h2>{{ count }}</h2>
          <button v-on:click="count = count + 1">Add</button>
          <button v-on:click="count = count - 1">Minus</button>
        </div>
        <div class="break1">
          <div>
            <h3>Method Handlers</h3>
            <!--07.B Event Handling : method Handlers -->
            <button class="button" @click="hello">Greet</button>
          </div>
        </div>
      </div>

      <div class="break">
        <!--08. Form Input Bindings A and B file : forms.vue -->
        <span class="heading">Form Input Bindings</span><br>
        <forms/>
      </div>

      <div class="break">
        <!--09. Watchers -->
        <h2>Volume Tracker(0 -20)</h2>
        <h4>Current Volume - {{ volume }}</h4>
        <div>
          <button class="button1" @click="volume += 2 ">Increase</button>
          <button class="button1" @click="volume -= 2 ">Decrease</button>
        </div>
      </div>

      <div class="break">
        <!--10. Components -->
        <span class="heading">Components</span><br>
        <div>
          <h3>Props and Emit</h3>
          <!--10. A and B Components : Props and Emit  file : props.vue-->
          <input type="text" v-model="firstname"/> 
          <input type="text" v-model="lastname"/>
        </div>
        <div>
          <props :firstname="firstname" :lastname="lastname" @callingevent="callingevent" />
        </div>
        <div class="break1">
          <h3>slots</h3>
          <slots/>
        </div>
      </div>

      <div class="break">
        <!--10. Routers file: router.vue/routerpage.vue/AboutView.vue/HomeView.view -->
        <span class="heading">Routers</span><br>
        <router/>
      </div>
    </div>
</template>

<script>
import { ref } from 'vue'
import reactivity from './reactivity.vue'
import computed from './computed.vue'
import listrendering from './listrendering.vue'
import forms from './forms.vue'
import props from './components/props.vue'
import slots from './components/slots.vue'
import router from './components/router.vue'

  export default {
    name: 'Greetings',
    components : {
    reactivity,
    computed,
    listrendering,
    forms,
    props,
    slots,
    router,
  },

  setup(){
    const firstname = ref('')
    const lastname = ref('')

    function callingevent(call) {
      alert(`Calling ${call}`)
    } 

    return{
      firstname,
      lastname,
      callingevent,

    }
  },

      data(){
      return {
        title: 'Hello Vue',/* 01.A*/
        htmlElement: '<h1 style="color:red">This is red</h1>',/* 01.B*/
        isDisabled: true,/* 01.C*/
        number: 5,/* 01.D*/
        fname: 'John',
        lname: 'Richardson',
        ok: true,/*02 */
        basemultipler: 2,
        status: 'danger',/*05.A*/
        emergency: 'exit',/*05.A*/
        textbackground: 'yellow',/*05.B*/
        titlesize: 30,
        /*07.A*/
        newname: 'Peter Parker',
        count: 0,
        /*09*/
        volume: 0,
        
      }
    },
    methods: {
      multiply(num) {
        return num * this.basemultipler
      },
      add(num1) {
        return num1 + 1
      },/* 07. Event Handling*/
      hello(event) {
        alert(`Hello ${name.value}!`)
        if(event){
          alert(event.target.tagName)
        }
      },
    },
    /*Watcher */
    watch: {
      volume(newValue, oldValue){
        if(newValue > oldValue && newValue === 16){
          alert('Your volume is too high')
        
        }
      }
    }
    
  }

  
</script>

<style scoped>
.break{
  margin-top: 50px;

}

.break1{
  margin-top: 10px;

}

.heading{
  font-weight: 600;
  font-size: 30px;
  color: aquamarine;
}

.danger{
  font-weight: 800;
  text-decoration: underline;
}

.exit{
  text-decoration:italic;
  font-size: 20px;
}

.red{
  color: red;
}

.green{
  color: green;
}

.title{
  font-weight: 600px;
  font-size: 30px;
}
header {
  line-height: 1.5;
  max-height: 100vh;
}

.button1 {
      background-color:rgb(0, 87, 164); 
      border: 2px;
      border-radius: 30px;
      color: white;
      padding: 16px 32px;
      text-align: center;
      text-decoration: none;
      display: inline-block;
      font-size: 16px;
      margin: 4px 2px;
      transition-duration: 0.4s;
      cursor: pointer;
    }


.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
