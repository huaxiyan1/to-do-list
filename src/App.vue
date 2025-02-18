<script setup>
import { ref } from 'vue';

    let str1=ref("")
    let list=ref([])
    let ID=ref(0)
   function enter(){
    list.value.push({isfinish:"item",
        test:str1.value,
    id:ID.value++})
    str1.value=''
   }
   function finish(id){
    for(let i=0;i<list.value.length;++i)
    if(list.value[i].id==id){
    list.value[i].isfinish=list.value[i].isfinish=="item"?"completed":"item"
    break;}
   }
    function del(id){
        for(let i=0;i<list.value.length;++i){
            if(list.value[i].id==id){
            console.log(list.value[i].isfinish,list.value[i].test);
            list.value.splice(i,1)
            break;
            }
        }
    
   
    
}
   
</script>
<template> 
    <div class="to-do">
        <div class="title">to-do list</div>
        <div class="todo-form">
            <input v-model="str1" @keyup.enter="enter" class="todo-input" type="text" placeholder="add a todo">
            <div @click="enter" class="todo-button">add</div>
        </div>
        <div class="box">
            <div v-for="i in list" :key="i.id" :class="[i.isfinish]">
            <input @click="finish(i.id)" class="check" type="checkbox">
            <div class="name">{{ i.test }}</div>
            <div @click="del(i.id)" class="del">del</div>
        </div>
    </div>
    </div>
</template>
<style>body{
    background-image: url("back.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    margin: 0;
    overflow: hidden;
    height: 100vh;
    /* background-color: aliceblue;  */
}
</style>
<style scoped>
    .to-do {
        position: absolute;
        top: 74%;
        left: 20%;
        width: 60%;
        height: 25%;
        background-color: white;
        border-radius: 10px;
        overflow: auto;
    }

    .title {
        position: relative;
        font-size: 30px;
        font-weight: 550;
        text-align: center;
        top: 5px;
    }

    .todo-form {
        display: flex;
        line-height: 28px;
        text-align: center;
    }

    .todo-input {
        position: relative;
        top: 10px;
        left: 5%;
        padding-left: 10px;
        border: 1px solid #dfe1e5;
        outline: none;
        width: 80%;
        height: 25px;
        border-radius: 20px 0 0 20px;
    }

    input::placeholder {
        font-size: 14.8px;
        color: #888;
    }

    .todo-button {
        position: relative;
        top: 10px;
        left: 0;
        right: 5%;
        outline: none;
        width: 10%;
        height: 28px;
        border-radius: 0 20px 20px 0;
        background-color: rgb(41, 125, 234);
        text-align: center;
        color: #ffff;
        cursor: pointer;
        font-size: 15px;
        user-select: none;
    }

    .item {
        position: relative;
        left: 10%;
        align-items: center;
        top: 10%;
        display: flex;
        width: 70%;
        height: 30px;
        border-radius: 20px;
        box-shadow: #dfe1e5 0 5px 8px;
        margin-bottom: 1.8%;
        background-color: white;
    }

    .check {
        position: relative;
        left: 1%;
    }

    .name {
        position: relative;
        left: 3%;

    }

    .del {
        position: absolute;
        right: 7%;
        cursor: pointer;
        user-select: none;
        color: rgb(226, 3, 3);
    }

    .completed {
        text-decoration: line-through;
        opacity: 0.4;
        position: relative;
        left: 10%;
        align-items: center;
        top: 10%;
        display: flex;
        width: 70%;
        height: 30px;
        border-radius: 20px;
        box-shadow: #dfe1e5 0 5px 8px;
        margin-bottom: 1.8%;
        background-color: white;
    }
    .box{
        position: absolute;
        top: 35%;
        left: 10%;
        width: 80%;
        height: 60%;
        background-color: white;
        border-radius: 10px;
        overflow: auto;
    }
</style>
