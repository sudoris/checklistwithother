<template>
  <div>

    <div id='example-3'>
    <span v-for="item in items" :key="item">
      <input type="checkbox" :id="item" :value="item" v-model="values">
      <label :for="item">{{item}}</label>
    </span>
    <input type="text" placeholder="Other..." v-on:keyup.13="add_item" v-model="other_val" style="margin-left:10px">
    <button v-if="other_val" v-on:click="add_item">+</button>
    </div>


    {{ values }}    
    
  </div>
</template>

<script>
export default {
  name: "Test",
  data() {
    return {
      def_items:['Chili','Salt','Butter'],
      values:[],
      other_val:''
    };
  },
  computed:{
    items(){
      return this.def_items.concat(this.values.filter((x)=> !this.def_items.includes(x)));
    }
  },
  methods: {
    add_item(){
      if (this.other_val){
        this.values.push(this.other_val)
        this.other_val=''
      }
      
    }
  }
};
</script>
