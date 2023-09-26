
<template>
    <div class="white">Hello {{ fullname }} </div>
    <button @click="callEvent">Call</button>
</template>

<script>
import { computed } from 'vue'
    export default{
        name: 'Greetings',
        setup(props, context)  {
            const fullname = computed(() => {
                return `${props.firstname} ${props.lastname}`
            })

            function callEvent() {
                context.emit('callingevent',fullname.value)
            }

            return {
                fullname,
                callEvent,            
            }

            
        },
        props: ['firstname','lastname'],
    }
</script>

<style>
    .white{
        color: aliceblue;
    }
</style>
