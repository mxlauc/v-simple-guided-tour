# V Simple Guided Tour
A simple guided tour for your Vue3 projects.

## Installation
### NPM
```
npm install v-simple-guided-tour
```

## Usage
Here is an example.

The VSimpleGuidedTour will be on button#id1, button#id3, button#id4 and finally button#id2.

```HTML
<template>
    <div id="app">

        <v-simple-guided-tour :steps="steps" :show="showGuide" @closed="dialogClosed" color="#FD650A" :labels="labels"/>

        <h1 style="text-align:center;">Press the button to show V Simple Guided Tour</h1>
        <button @click="showGuide = true">Show guide</button>

        <button id="id1">Dummy button 1</button>
        <button id="id2">Dummy button 2</button>
        <button id="id3">Dummy button 3</button>
        <button id="id4">Dummy button 4</button>
        
    </div>
</template>

<script>
import { defineComponent } from 'vue';
import VSimpleGuidedTour from '@/v-simple-guided-tour.vue';

export default defineComponent({
    name: 'ServeDev',
    components: {
        VSimpleGuidedTour
    },
    data(){
        return {
            showGuide: false,
            labels : {
                prev: "Prev.",
                next: "Next",
                close: "Close now",
            },
            steps : [
                {
                    selector: "#id1",
                    title: "Welcome",
                    description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fex nisi, vel delectus nobis facilis fugit suscipit consequatur!"
                },
                {
                    selector: "#id3",
                    title: "Another tip",
                    description: "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Gerendis, voluptate illum nisi repellat adipisci?"
                },
                {
                    selector: "#id4",
                    title: "Another tip",
                    description: "Lorem ipsum dolor sit amet consectetur adipisicing elit."
                },
                {
                    selector: "#id2",
                    title: "That's all",
                    description: "Lorem ipsum dolor?"
                }
            ]
        };
    },
    methods:{
        dialogClosed(){
            this.showGuide = false;
        }
    },
});
</script>
```

# Options

| Option | Description |
| ----- | ----- |
| steps | Array (default = {}) - an array of objects, they represents the steps of the tour. |
| show | Boolean (default = true) - If it is true, the dialog is shown on step one. If it is false, the dialog is removed from DOM. See @click on Show Guide button.|
| closed | Event that is fired when the dialog is closed by user. You must create a dialogClosed method, in order to dialog can be seen again when user clicks the Show Guide button.|
| color | String (default = "#15DBB7") - The color of title, progressbar and buttons next and prev.|
| labels | Object (default = { prev: "Previous", next: "Next", close: "Close" }) - Those are the texts to show on prev, next and close buttons (Use it if you want to show other text or if you are working in Spanish or other languages).|

## Authors
[@mxlauc](https://github.com/mxlauc)