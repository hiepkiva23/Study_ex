<template>
  <div>
    <h2>Danh sách công việc</h2>
    <ul>
      <li
        v-for="(item,index) in items"
        :key="index"
        draggable="true"
        @dragstart ="handStart(index)"
        @dragover.prevent
        @drop = "handleDrop(index)"
        style="list-style: none;"  
      >
      <div class="drag-item" style="display: flex;  align-items: center; justify-content: center; text-align: center; ">     
             <img
          :src="item.src"
          style="display: block; width: 100px; height: 100px; object-fit: cover; border-radius: 10px; margin-bottom: 10px;"
        />
        <h3>{{ item.name }}</h3>     
        <p>{{ item.project }}</p>
      </div>     
      </li> 
    </ul>
  </div>
</template>

<script>


export default {
 data() {
    return {
      items: [
        {src: "/images/10.jpg", id: 1, name: 'Công việc 1', project: 'Dự án A'},
        {src: "/images/11.jpg", id: 2, name: 'Công việc 2', project: 'Dự án B'},
        {src: "images/12.png", id: 3, name: 'Công việc 3', project: 'Dự án C'},
      ],
      draItemIndex: null,
    };
  },
  methods: {
    handStart(index){
      this.draItemIndex = index;
    },

      handleDrop(index){
        const contentItemcr = this.items[this.draItemIndex];
        this.items.splice(this.draItemIndex, 1);
        this.items.splice(index, 0, contentItemcr);
        this.draItemIndex = null;
      }
   }
 
  }

</script>

<style>

</style>