<template>
    <div>
    <!--08.A - Form Input Bindings -->
        input type : text
        <p>Message is: {{ message }}</p>
        <input v-model="message" placeholder="edit me" />
        <br>

        input type : checkbox <br>
        <input type="checkbox" id="checkbox" v-model="checked" />
        <label for="checkbox">{{ checked }}</label> <br>

        input type : radio <br>
        Gender: {{ Gender }}<br>
        <input type="radio" id="male" value="Male" v-model="Gender" />
        <label for="male">Male</label>

        <input type="radio" id="female" value="Female" v-model="Gender" />
        <label for="female">Female</label> <br>

        input type : select <br>
        <span> Category: {{ category }}</span> <br>

        <select v-model="category">
        <option value="Action">Action</option>
        <option value="Romance">Romance</option>
        <option value="Comedy">Comedy</option>
        </select><br>

        input type : Textarea <br>
        <span>Type your message:</span><br>
        <p style="white-space: pre-line;">{{ messages }}</p>
        <textarea v-model="messages" placeholder="your message"></textarea>

    </div>
    <hr>
    <div class="break1">
        <!--08.B - Form Input Bindings -->
        input type : text.lazy
        <p>Message is: {{ lazy }}</p>
        <input v-model.lazy="lazy" placeholder="edit me" />
        <br>

        input type : text.number {{ age }}
        <input v-model.number="age" />
        <br>

        input type : text.trim
        Final : {{ msg }}
        <input v-model.trim="msg" />
  </div>

</template>

<script>
export default {
    data() {
        return{
            message:'',
            messages:'',
            lazy:'',
            checked: true,
            Gender: 'Male',
            category: '',
            msg: '',
            age:0,
            volume: 0,
        }
    }
}

</script>