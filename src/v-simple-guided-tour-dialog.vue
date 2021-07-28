<template>
  <div class="vsgt-dialog" ref="popper" :style="getCssColor">
      <div id="vsgt-arrow" data-popper-arrow></div>
      <div class="vsgt-container-border">
        <div class="vsgt-container">
          <div class="vsgt-close-button" @click="close">
            <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" fill="currentColor" viewBox="0 0 16 16">
              <path d="M1.293 1.293a1 1 0 0 1 1.414 0L8 6.586l5.293-5.293a1 1 0 1 1 1.414 1.414L9.414 8l5.293 5.293a1 1 0 0 1-1.414 1.414L8 9.414l-5.293 5.293a1 1 0 0 1-1.414-1.414L6.586 8 1.293 2.707a1 1 0 0 1 0-1.414z"/>
            </svg>
          </div>
          <h3 class="vsgt-m-0 vsgt-mb-3 vsgt-title" >
            {{data.title}}
          </h3>  
          <p class="vsgt-m-0">
            {{data.description}}
          </p>
        </div>
      </div>
      <div>
        <div class="vsgt-row vsgt-footer">
          <div class="vsgt-col-auto vsgt-counter">
            {{currentStep + 1}} / {{totalSteps}}
          </div>
          <div class="vsgt-col vsgt-vertical-center">
            <div class="vsgt-progressbar">
              <div class="vsgt-progress" :style="{width: getProgressWidth + '%'}">
              </div>
            </div>
          </div>
          <div class="vsgt-col-auto">
            <button class="vsgt-btn" @click="prev" :style="{visibility: currentStep == 0 ? 'hidden' : 'visible'}">{{labels.prev}}</button>
            <button class="vsgt-btn" @click="next">
              {{(currentStep + 1) < totalSteps ? labels.next : labels.close}}
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
    labels: {
      type: Object
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
                offset: [0, 20],
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
<style scoped>
  .vsgt-m-0{
    margin: 0px;
  }
  .vsgt-p-0{
    padding: 0px;
  }
  .vsgt-mb-3{
    margin-bottom: 1rem;
  }
  .vsgt-dialog{
    border-radius: 4px;
    width: 400px;
    max-width: 100%;
    box-shadow: 2px 4px 10px rgba(0, 0, 0, 0.25);
  }
  .vsgt-title{
    color:var(--color);
  }
  .vsgt-container-border{
    border-top-right-radius: 4px;
    border-top-left-radius: 4px;
    overflow: hidden;
    z-index: -2;
    
    border-left: 1px solid #ccc;
    border-top: 1px solid #ccc;
    border-right: 1px solid #ccc;
    background-color: #fff;
  }
  .vsgt-container{
    border-top-right-radius: 4px;
    border-top-left-radius: 4px;
    overflow: hidden;
    position: relative;
    z-index: 10000;
    padding: 1rem;
    background-color: #fff;
  }
  .vsgt-counter{
    padding: 0.75rem;
    padding-right:0;
    font-weight:bold;
    color:#fff;
  }
  .vsgt-row{
    display: flex;
    width: 100%;
    flex-wrap:wrap
  }
  .vsgt-col{
    max-width:100%;
    flex-grow:1;
    flex-basis:0;
    position:relative
  }
  .vsgt-col-auto{
    flex: 0 0 auto;
    width: auto;
    max-width: none;
  }
  .vsgt-progressbar{
    margin: 0px 10px;
    width: 100%;
    background-color: #15DBB7;
    background-color: var(--color);
    border-radius: 4px;
    height: 8px;
    overflow: hidden;
  }
  .vsgt-progress{
    background-color: #fff;
    height: 100%;
    border-radius: 4px;
    transition: width 0.2s ease-out;
    transition-delay: 0.3s;
  }
  .vsgt-close-button{
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
  .vsgt-close-button:hover{
    background-color: #ddd;
  }
  .vsgt-close-button:active{
    background-color: #999;
  }
  .vsgt-btn{
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
  .vsgt-btn:hover{
    background-color: #45455c;
  }
  .vsgt-btn:active{
    background-color: #000;
  }
  .vsgt-footer{
    border-bottom-right-radius: 4px;
    border-bottom-left-radius: 4px;
    
    overflow: hidden;
    position: relative;
    background-color:#42424E;
  }
  .vsgt-vertical-center{
    display: flex;
    align-items: center;
  }

#vsgt-arrow,
#vsgt-arrow::before {
  z-index: 0;
  border: 1px solid #ddd;
  
  position: absolute;
  width: 50px;
  height: 50px;
  background: inherit;
}

#vsgt-arrow {
  visibility: hidden;
  
}

#vsgt-arrow::before {
  background-color: #fff;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  visibility: visible;
  content: '';
  transform: rotate(45deg);
}
.vsgt-dialog[data-popper-placement^='top'] > #vsgt-arrow::before {
  background-color:#42424E;
}
.vsgt-dialog[data-popper-placement^='top'] > #vsgt-arrow {
  bottom: -4px;
}

.vsgt-dialog[data-popper-placement^='bottom'] > #vsgt-arrow {
  top: -4px;
}

.vsgt-dialog[data-popper-placement^='left'] > #vsgt-arrow {
  right: -4px;
}

.vsgt-dialog[data-popper-placement^='right'] > #vsgt-arrow {
  left: -4px;
}
</style>
