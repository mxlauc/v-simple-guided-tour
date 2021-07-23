<template>
  <div class="dialog" ref="popper" :style="getCssColor">
      <div id="arrow" data-popper-arrow></div>


      <div class="container-border">
        <div class="container">
          <div class="close-button" @click="close">
            <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" fill="currentColor" viewBox="0 0 16 16">
              <path d="M1.293 1.293a1 1 0 0 1 1.414 0L8 6.586l5.293-5.293a1 1 0 1 1 1.414 1.414L9.414 8l5.293 5.293a1 1 0 0 1-1.414 1.414L8 9.414l-5.293 5.293a1 1 0 0 1-1.414-1.414L6.586 8 1.293 2.707a1 1 0 0 1 0-1.414z"/>
            </svg>
          </div>
          <h3 class="m-0 mb-3 title" >
            {{data.title}}
          </h3>  
          <p class="m-0">
            {{data.description}}
          </p>
        </div>
      </div>
      <div>
        <div class="row footer">
          <div class="col-auto counter">
            {{currentStep + 1}} / {{totalSteps}}
          </div>
          <div class="col vertical-center">
            <div class="progressbar">
              <div class="progress" :style="{width: getProgressWidth + '%'}">
              </div>
            </div>
          </div>
          <div class="col-auto">
            <button class="btn" @click="prev" :style="{visibility: currentStep == 0 ? 'hidden' : 'visible'}">previous</button>
            <button class="btn" @click="next">
              {{(currentStep + 1) < totalSteps ? 'next' : 'close'}}
            </button>
          </div>
        </div>
      </div>
    </div>
</template>


<script>
import { defineComponent } from 'vue';
import { createPopper } from '@popperjs/core';
import jump from 'jump.js'

export default defineComponent({
  name: 'VSimpleGuidedTourDialog', 
  data() {
    return {
      
    };
  },
  props: {
    data : {
      type: Object,
      default: {},
    },
    currentStep: {
      type: Number,
      default: 0,
    },
    totalSteps: {
      type: Number,
      default: 0,
    },
    color: {
      type: String,
      default: "#15DBB7",
    },
  },
  watch:{
    data(newData){
      this.showDialog();
    }
  },
  mounted(){
    this.showDialog();
    
  },
  computed: {
    getProgressWidth(){
      return Math.round((this.currentStep + 1) / this.totalSteps * 100);
    },
    getCssColor(){
      return {
        '--color': this.color,
      }
    }
  },
  methods: {
    showDialog(){
      let target = document.querySelector(this.data.selector);
      let popper = createPopper(target, this.$refs.popper, {
          placement: 'bottom',
          modifiers: [
            {
              name: 'offset',
              options: {
                offset: [0, 30],
              },
            },
            
          ],

      });
      jump(this.data.selector, {
        offset: -300,
        duration: 500,
      });
      popper.update();
    },
    prev(){
      this.$emit("prev");
    },
    next(){
      this.$emit("next");
    },
    close(){
      this.$emit("close");
    },
  },
  emits: [
    "prev",
    "next",
    "close",
  ],
});
</script>
<style>
body{
  background-color: #fff;
}
</style>
<style scoped>
  .m-0{
    margin: 0px;
  }
  .p-0{
    padding: 0px;
  }
  .mb-3{
    margin-bottom: 1rem;
  }
  .dialog{
    border-radius: 4px;
    width: 400px;
    max-width: calc(100% - 100px);
    box-shadow: 2px 4px 10px rgba(0, 0, 0, 0.25);
  }
  .title{
    color:var(--color);
  }
  .container-border{
    border-top-right-radius: 4px;
    border-top-left-radius: 4px;
    overflow: hidden;
    z-index: -2;
    
    border-left: 1px solid #ccc;
    border-top: 1px solid #ccc;
    border-right: 1px solid #ccc;
    background-color: #fff;
  }
  .container{
    border-top-right-radius: 4px;
    border-top-left-radius: 4px;
    overflow: hidden;
    position: relative;
    z-index: 10000;
    padding: 1rem;
    background-color: #fff;
  }
  .counter{
    padding: 0.75rem;
    padding-right:0;
    font-weight:bold;
    color:#fff;
  }
  .row{
    display: flex;
    width: 100%;
    flex-wrap:wrap
  }
  .col{
    max-width:100%;
    flex-grow:1;
    flex-basis:0;
    position:relative
  }
  .col-auto{
    flex: 0 0 auto;
    width: auto;
    max-width: none;
  }
  .progressbar{
    margin: 0px 10px;
    width: 100%;
    background-color: #15DBB7;
    background-color: var(--color);
    border-radius: 4px;
    height: 8px;
    overflow: hidden;
  }
  .progress{
    background-color: #fff;
    height: 100%;
    border-radius: 4px;
    transition: width 0.2s ease-out;
    transition-delay: 0.3s;
  }
  .close-button{
    float:right;
    margin: 0 0 0.5rem 0.5rem;
    color: #666;
    border-radius: 50%;
    padding: 10px;
    height: 14px;
    width: 14px;
    transition: background-color 0.2s ease-out;
    background-color: #eee;
  }
  .close-button:hover{
    background-color: #ddd;
  }
  .close-button:active{
    background-color: #999;
  }
  .btn{
    height: 100%;
    padding: 0.75rem;
    text-transform: uppercase;
    font-weight:bold;
    background-color: #262632;
    color:var(--color);
    cursor: pointer;
    border: none;
    outline: none;
    transition: background-color 0.2s ease-out;
  }
  .btn:hover{
    background-color: #45455c;
  }
  .btn:active{
    background-color: #000;
  }
  .footer{
    border-bottom-right-radius: 4px;
    border-bottom-left-radius: 4px;
    
    overflow: hidden;
    position: relative;
    background-color:#42424E;
  }
  .vertical-center{
    display: flex;
    align-items: center;
  }

  #arrow,
#arrow::before {
  z-index: 0;
  border: 1px solid #ddd;
  
  position: absolute;
  width: 50px;
  height: 50px;
  background: inherit;
}

#arrow {
  visibility: hidden;
  
}

#arrow::before {
  background-color: #fff;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  visibility: visible;
  content: '';
  transform: rotate(45deg);
}
.dialog[data-popper-placement^='top'] > #arrow::before {
  background-color:#42424E;
}
.dialog[data-popper-placement^='top'] > #arrow {
  bottom: -4px;
}

.dialog[data-popper-placement^='bottom'] > #arrow {
  top: -4px;
}

.dialog[data-popper-placement^='left'] > #arrow {
  right: -4px;
}

.dialog[data-popper-placement^='right'] > #arrow {
  left: -4px;
}
</style>
