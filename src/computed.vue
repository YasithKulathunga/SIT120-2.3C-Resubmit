<script>
    export default{
        data(){
            return {
                fname: 'John',
                lname: 'Richardson'
            }
        },

        computed: {
            fullname(){
            return `${this.fname} ${this.lname}`
            }
        },
    }
</script>
<template>
    <!--04. Computed Properties-->
    {{ fullname }}
</template>