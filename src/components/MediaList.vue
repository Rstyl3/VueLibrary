<template>
  <div id="media-list">
      <h1>{{ title }}</h1>
      <select @change="filterList" >
        <option value="">Select a type of media...</option>
        <option v-for="item in uniqueItemsList" :key="item.id">{{item}}</option>
      </select>
      <ul>
        <li v-show="type === '' || type === media.type" 
            v-for="media in mediaList" :key="media.id" 
            :class="[media.showDetail ? 'less': 'more', media.type]"
            @click="toggleDetails(media)" >
          <h3>{{media.title}}</h3> 
          <div v-show="media.showDetail">
            <p>{{media.description}}</p>
            <p v-if="media.contributor" class="byline">By: {{media.contributor}}</p>
          </div>
        </li>
      </ul>
  </div>
</template>

<script>
import media from "../data/app.js";

export default {
  name: "MediaList",
  data() {
    return {
      title: "Treehouse Public Library",
      mediaList: media,
      type: ""
    };
  },
  methods: {
    toggleDetails(media) {
      media.showDetail = !media.showDetail;
    },
    filterList() {
      this.type = event.target.value
    }
  },
  computed:{
    uniqueItemsList(){
      const types = []
      this.mediaList.forEach((item)=> {
        if(!types.includes(item.type)){
          types.push(item.type)
        }
      })
      return types
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
