<template>
  <v-simple-guided-tour-dialog
    v-if="showDialog"
    :data="steps[currentStep]"
    :current-step="currentStep"
    :total-steps="steps.length"
    :color="color"
    @prev="prev"
    @next="next"
    @close="close"/>
</template>


<script>
import { defineComponent } from 'vue';
import VSimpleGuidedTourDialog from './v-simple-guided-tour-dialog.vue';
import jump from 'jump.js'

export default defineComponent({
  name: 'VSimpleGuidedTour', 
  components: {
    VSimpleGuidedTourDialog,
  },
  data() {
    return {
      currentStep : 0,
      showDialog : this.show,
    };
  },
  props: {
    steps : {
      type: Object,
      default :{},
    },
    show: {
      type: Boolean,
      default: true,
    },
    color: {
      type: String,
      default: "#15DBB7",
    },
  },
  emits:[
    "closed"
  ],
  watch:{
    show(newValue){
      this.showDialog = newValue;
    }
  },
  methods: {
    prev(){
      if(this.currentStep > 0){
        this.currentStep--;
      }
    },
    next(){
      if(this.currentStep < this.steps.length - 1){
        this.currentStep++;
      }else{
        this.close();
      }
    },
    close(){
      jump("body", {
        offset: -300,
        duration: 500,
      });
      this.showDialog = false;
      this.currentStep = 0;
      this.$emit("closed");
    },
  },
});
</script>

<style scoped>
  
</style>
