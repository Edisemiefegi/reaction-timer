<template>
  <div class="block" v-if="showblock" @click="stoptimer">
    click me
  </div>
</template>

<script>
export default {
    props: ['Delay'],
    data(){
        return{
            showblock: false,
            timer: null,
            reactiontime: 0
        }
    },
    mounted(){
        setTimeout(() => {
            this.showblock = true
            this.starttimer()
        }, this.Delay)
    },
    methods: {
        starttimer(){
            this.timer = setInterval(() => {
                this.reactiontime += 10
            }, 10)
        },
        stoptimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactiontime)
        }
    }
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>