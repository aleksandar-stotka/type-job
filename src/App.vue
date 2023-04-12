<template>
  <div class="app">
   <JobsList :jobs="jobs"/>
  </div>
</template>

<script lang="ts">
import { defineComponent,reactive, ref, toRefs} from 'vue';
import job from "./types/job"
import JobsList from './components/JobsList.vue';
export default defineComponent({
  name: 'App',
  components: {JobsList},
  setup() {
    
   const jobs = ref<job[]>([
    {title:'farm worker',location:'san francisko',salary:333,id:"1"},
    {title:'drumer',location:'d hisar',salary:223,id:"2"},
    {title:'pro bike',location:'Bitola',salary:1000,id:"3"},
    {title:'eri worker',location:'Struga',salary:333,id:"4"},
    {title:'guitarist',location:'Belgrad',salary:444,id:"5"}
   ])
     return {jobs}
  },
 
 
});
</script>

<style>

</style>
