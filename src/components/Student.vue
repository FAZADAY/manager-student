<template>
    <div>
        <div>
            <label for="">Tên:</label>
            <input type="text" v-model="student.name">
        </div>
         <div>
            <label for="">Tuổi:</label>
            <input type="text" v-model="student.age">
        </div>
         <div>
            <label for="">Số điện thoại</label>
            <input type="text" v-model="student.phone">
        </div>
         <div>
            <label for="">Địa chỉ:</label>
            <input type="text" v-model="student.address">
        </div>
        <input type="button" value="Add" @click="clickAdd">
    </div>
</template>

<script>
import { watch } from '@vue/runtime-core'
export default {
    props: {
        itemEdit:{
            type: Object,
            default: null
        }
        
    },
    watch: {
       itemEdit() {
         if(this.itemEdit){
            this.student = Object.assign({},this.itemEdit) 
        }else{
            this.student = {}
        }
       }
    },
    methods: {
        clickAdd(){
            this.$emit("save",this.student)
            this.student = {
                id: Math.floor(Math.random()*10000),
                name:"",
                age:"",
                phone:"",
                address:""
            }
        }
    },
    data() {
        return{
            student:{
                id: Math.floor(Math.random()*10000),
                name:"",
                age:"",
                phone:"",
                address:""
            }
        }
    }
}
</script>

<style scoped>
    div{
        padding: 5px;
    }
    input[type="button"] {
        background:  green;
        color: #fff;
        border: 5px solid #0000;
        border-radius: 5px;
        cursor: pointer;
    }
</style> 