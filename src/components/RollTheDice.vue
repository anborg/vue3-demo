<template>
    <h2> Roll The dice</h2>
    <button @click="roll()">Roll #{{rolls.length}}</button>
    <button @click="reset()">Reset</button>
    <div> Number: {{dice}} Total: {{total}} </div>
    <ul>
        <li v-for="(t, index) in rolls" :key="index">
            {{t}}
        </li>
    </ul>

</template>
<script lang="ts">
import{ref,computed} from 'vue'
export default {
    name: 'RollTheDice',
    setup(){
        const dice = ref(0)
        const rolls = ref([])

        function roll(){
            dice.value = Math.floor(Math.random() * Math.floor(5)) +1;
            rolls.value.unshift(dice.value);
        }
        function reset(){
            dice.value = 0
            rolls.value = []
        }
        const total=computed(()=>{
            let temptotal = 0
            for(let i=0; i < rolls.value.length; i++){
                temptotal += rolls.value[i]
            }
            return temptotal
        });//computed
        return {dice, rolls, total, roll, reset}
    }//setup
}//default
</script>