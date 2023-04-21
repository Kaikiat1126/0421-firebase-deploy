<template>
  <div>
    <Table :data="computedData" />
    <br><br>
    <Answer :alpha="computedAlpha" :beta="computedBeta" :charlie="computedCharlie" />
  </div>
</template>

<script >
  import Table from './components/Table.vue'
  import Answer from './components/Answer.vue'
  import { ref,reactive, onMounted,computed } from 'vue';

  export default {
    setup(){
      let data = reactive([])
      let alpha = ref(0)
      let beta = ref(0)
      let charlie = ref(0)

      function getAlpha(){
        let ans = 0
        for(let i = 0; i < data.value.length; i++){
          if(data.value[i].index == 'A5' || data.value[i].index == 'A20'){
            ans += data.value[i].value
          }
        }
        console.log('Alpha: ', ans);
        alpha.value = ans
      }

      function getBeta(){
        let A15 = 0
        let A7 = 0
        for(let i = 0; i < data.value.length; i++){
          if(data.value[i].index == 'A15'){
            A15 = data.value[i].value
          }
          if(data.value[i].index == 'A7'){
            A7 = data.value[i].value
          }
        }
        console.log('Beta: ', A15 / A7);
        beta.value = A15 / A7
      }

      function getCharlie(){
        let A13 = 0
        let A12 = 0

        for(let i = 0; i < data.value.length; i++){
          if(data.value[i].index == 'A13'){
            A13 = data.value[i].value
          }
          if(data.value[i].index == 'A12'){
            A12 = data.value[i].value
          }
        }

        console.log('Charlie: ', A13 * A12);
        charlie.value = A13 * A12
      }

      const computedData = computed(() => {
        return data.value
      })

      const computedAlpha = computed(() => {
        return alpha.value
      })

      const computedBeta = computed(() => {
        return beta.value
      })

      const computedCharlie = computed(() => {
        return charlie.value
      })

      async function fetchData() {
        try {
          const response = await fetch("data.json");
          const result = await response.json();
          data.value = result.items;
          getAlpha()
          getBeta()
          getCharlie()
        } catch (error) {
          console.log(error);
        }
      }

      onMounted(()=>{
        fetchData()
      })

      return {
        computedData,
        computedAlpha,
        computedBeta,
        computedCharlie
      }
    },
    components: {
      Table,
      Answer
    }
  }
</script>