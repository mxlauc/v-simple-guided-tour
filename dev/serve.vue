<template>
  <div id="app" style="padding: 100px 15%">
    <v-simple-guided-tour :steps="steps" :show="showGuide" @closed="dialogClosed"/>

    <h1 style="text-align:center;">Press the button to show V Simple Guided Tour</h1>

    <button @click="showGuide = true">Show guide</button>

    <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit.</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Placeat, doloremque culpa facilis quibusdam accusantium eveniet aliquam molestias vitae pariatur sit, labore ut. Necessitatibus nesciunt quisquam iusto ratione sit numquam veritatis?
    Reprehenderit incidunt distinctio neque quos velit esse sit dolore delectus similique? Error repellat pariatur magni fugit ex sed, perspiciatis tempore quos reprehenderit? Labore sint, pariatur hic ad adipisci architecto sequi?
    Recusandae eum dolores laudantium ratione obcaecati assumenda quidem ullam accusantium! Numquam quae iusto corrupti, dolore, perferendis reiciendis veniam obcaecati, amet consequuntur aspernatur eaque nam repudiandae voluptate voluptates officia quas saepe.
    Explicabo unde illum magnam, tempora blanditiis amet laborum sunt! Voluptatem dicta laborum quo, exercitationem dolorem laboriosam laudantium distinctio ea adipisci vel. Earum ut pariatur illo ipsam iure delectus. Et, fugiat.</p>
    <h1>Culpa similique quis voluptatibus tempore fuga</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa similique quis voluptatibus tempore fuga nemo excepturi rem optio quibusdam obcaecati totam ex nisi, vel delectus nobis facilis fugit suscipit consequatur!</p>

    <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit.</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Placeat, doloremque culpa facilis quibusdam accusantium eveniet aliquam molestias vitae pariatur sit, labore ut. Necessitatibus nesciunt quisquam iusto ratione sit numquam veritatis?
    Reprehenderit incidunt distinctio neque quos velit esse sit dolore delectus similique? Error repellat pariatur magni fugit ex sed, perspiciatis tempore quos reprehenderit? Labore sint, pariatur hic ad adipisci architecto sequi?
    Recusandae eum dolores laudantium ratione obcaecati assumenda quidem ullam accusantium! Numquam quae iusto corrupti, dolore, perferendis reiciendis veniam obcaecati, amet consequuntur aspernatur eaque nam repudiandae voluptate voluptates officia quas saepe.
    Explicabo unde illum magnam, tempora blanditiis amet laborum sunt! Voluptatem dicta laborum quo, exercitationem dolorem laboriosam laudantium distinctio ea adipisci vel. Earum ut pariatur illo ipsam iure delectus. Et, fugiat.</p>
    <h1>Culpa similique quis voluptatibus tempore fuga</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa similique quis voluptatibus tempore fuga nemo excepturi rem optio quibusdam obcaecati totam ex nisi, vel delectus nobis facilis fugit suscipit consequatur!</p>

    <button id="id1">Dummy button 1</button>

    <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit.</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Placeat, doloremque culpa facilis quibusdam accusantium eveniet aliquam molestias vitae pariatur sit, labore ut. Necessitatibus nesciunt quisquam iusto ratione sit numquam veritatis?
    Reprehenderit incidunt distinctio neque quos velit esse sit dolore delectus similique? Error repellat pariatur magni fugit ex sed, perspiciatis tempore quos reprehenderit? Labore sint, pariatur hic ad adipisci architecto sequi?
    Recusandae eum dolores laudantium ratione obcaecati assumenda quidem ullam accusantium! Numquam quae iusto corrupti, dolore, perferendis reiciendis veniam obcaecati, amet consequuntur aspernatur eaque nam repudiandae voluptate voluptates officia quas saepe.
    Explicabo unde illum magnam, tempora blanditiis amet laborum sunt! Voluptatem dicta laborum quo, exercitationem dolorem laboriosam laudantium distinctio ea adipisci vel. Earum ut pariatur illo ipsam iure delectus. Et, fugiat.</p>
    <h1>Culpa similique quis voluptatibus tempore fuga</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa similique quis voluptatibus tempore fuga nemo excepturi rem optio quibusdam obcaecati totam ex nisi, vel delectus nobis facilis fugit suscipit consequatur!</p>
    
    <button id="id2">Dummy button 2</button>
    
    <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit.</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Placeat, doloremque culpa facilis quibusdam accusantium eveniet aliquam molestias vitae pariatur sit, labore ut. Necessitatibus nesciunt quisquam iusto ratione sit numquam veritatis?
    Reprehenderit incidunt distinctio neque quos velit esse sit dolore delectus similique? Error repellat pariatur magni fugit ex sed, perspiciatis tempore quos reprehenderit? Labore sint, pariatur hic ad adipisci architecto sequi?
    Recusandae eum dolores laudantium ratione obcaecati assumenda quidem ullam accusantium! Numquam quae iusto corrupti, dolore, perferendis reiciendis veniam obcaecati, amet consequuntur aspernatur eaque nam repudiandae voluptate voluptates officia quas saepe.
    Explicabo unde illum magnam, tempora blanditiis amet laborum sunt! Voluptatem dicta laborum quo, exercitationem dolorem laboriosam laudantium distinctio ea adipisci vel. Earum ut pariatur illo ipsam iure delectus. Et, fugiat.</p>
    <h1>Culpa similique quis voluptatibus tempore fuga</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa similique quis voluptatibus tempore fuga nemo excepturi rem optio quibusdam obcaecati totam ex nisi, vel delectus nobis facilis fugit suscipit consequatur!</p>

    <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit.</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Placeat, doloremque culpa facilis quibusdam accusantium eveniet aliquam molestias vitae pariatur sit, labore ut. Necessitatibus nesciunt quisquam iusto ratione sit numquam veritatis?
    Reprehenderit incidunt distinctio neque quos velit esse sit dolore delectus similique? Error repellat pariatur magni fugit ex sed, perspiciatis tempore quos reprehenderit? Labore sint, pariatur hic ad adipisci architecto sequi?
    Recusandae eum dolores laudantium ratione obcaecati assumenda quidem ullam accusantium! Numquam quae iusto corrupti, dolore, perferendis reiciendis veniam obcaecati, amet consequuntur aspernatur eaque nam repudiandae voluptate voluptates officia quas saepe.
    Explicabo unde illum magnam, tempora blanditiis amet laborum sunt! Voluptatem dicta laborum quo, exercitationem dolorem laboriosam laudantium distinctio ea adipisci vel. Earum ut pariatur illo ipsam iure delectus. Et, fugiat.</p>
    <h1>Culpa similique quis voluptatibus tempore fuga</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa similique quis voluptatibus tempore fuga nemo excepturi rem optio quibusdam obcaecati totam ex nisi, vel delectus nobis facilis fugit suscipit consequatur!</p>

    <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit.</h1>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Placeat, doloremque culpa facilis quibusdam accusantium eveniet aliquam molestias vitae pariatur sit, labore ut. Necessitatibus nesciunt quisquam iusto ratione sit numquam veritatis?
    Reprehenderit incidunt distinctio neque quos velit esse sit dolore delectus similique? Error repellat pariatur magni fugit ex sed, perspiciatis tempore quos reprehenderit? Labore sint, pariatur hic ad adipisci architecto sequi?
    Recusandae eum dolores laudantium ratione obcaecati assumenda quidem ullam accusantium! Numquam quae iusto corrupti, dolore, perferendis reiciendis veniam obcaecati, amet consequuntur aspernatur eaque nam repudiandae voluptate voluptates officia quas saepe.
    Explicabo unde illum magnam, tempora blanditiis amet laborum sunt! Voluptatem dicta laborum quo, exercitationem dolorem laboriosam laudantium distinctio ea adipisci vel. Earum ut pariatur illo ipsam iure delectus. Et, fugiat.</p>

    <button id="id3">Dummy button 3</button>

    <h1>Culpa similique quis voluptatibus tempore fuga</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa similique quis voluptatibus tempore fuga nemo excepturi rem optio quibusdam obcaecati totam ex nisi, vel delectus nobis facilis fugit suscipit consequatur!</p>


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
      steps : [
        {
          selector: "#id1",
          title: "Welcome",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa similique quis voluptatibus tempore fuga nemo excepturi rem optio quibusdam obcaecati totam ex nisi, vel delectus nobis facilis fugit suscipit consequatur!"
        },
        {
          selector: "#id3",
          title: "Another tip",
          description: "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Corrupti maiores reprehenderit fugiat repellat, quae optio at tempora tenetur non suscipit laborum! Ipsam ducimus placeat perferendis, voluptate illum nisi repellat adipisci?"
        },
        {
          selector: "#id4",
          title: "Another tip",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa similique quis voluptatibus tempore fuga nemo excepturi rem optio quibusdam obcaecati totam ex nisi, vel delectus nobis facilis fugit suscipit consequatur!"
        },
        {
          selector: "#id2",
          title: "That's all",
          description: "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Corrupti maiores reprehenderit fugiat repellat, quae optio at tempora tenetur non suscipit laborum! Ipsam ducimus placeat perferendis, voluptate illum nisi repellat adipisci?"
        }
      ]
    };
  },
  mounted(){
    
  },
  methods:{
    dialogClosed(){
      this.showGuide = false;
    }
  },
});
</script>
<style>
*{
  font-family: sans-serif;
}
</style>