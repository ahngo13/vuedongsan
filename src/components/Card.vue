<template>
  <div>
    <img class="room-img" :src="item.image"/>
    <h4 @click="openModal(item)">{{ item.title }}</h4>
    <p>{{ item.price }}만원</p>
    <button @click="()=>increase(item.id)">허위매물 신고</button><span>신고수 : {{item.count}}</span>
  </div>
</template>
  
<script>

  export default {
    name : 'CardDiv',
    props : {
        item : Object,
        isShowModal : Boolean,
        selectedIndex : Number,
    },
    methods:{
        openModal (){
            this.$emit('openModal', this.item);
        }
    }
  }
</script>
<style>
    
</style>