<template>
  <div>
    <h1>Quản lí sinh viên</h1>
    <Student :itemEdit="hocsinh" @save="clickSave" />
      <form action="" class="table">
        <table>
          <thead>
            <tr>
              <th>Id</th>
              <th>Tên</th>
              <th>Tuổi</th>
              <th>Số điện thoại</th>
              <th>Địa chỉ</th>
              <th>Chức năng</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in list" :key="item.id">
              <th>{{item.id}}</th>       
              <th>{{item.name}}</th>
              <th>{{item.age}}</th>
              <th>{{item.phone}}</th>
              <th>{{item.address}}</th>
              <th>
                <td><input type="button" value="Edit" @click="clickEdit(item)"></td>
                <td> <input type="button" value="Delete" @click="clickDelete(item)"></td>
              </th>
            </tr>
          </tbody>
        </table>
      </form>
  </div>
</template>

<script>
import Student from "./Student.vue"
export default {
  components: {
    Student: Student
  },
  methods: {
    clickSave(itemSave){
        let index = this.list.findIndex((c)=>c.id === itemSave.id)
        if(index >= 0) {
          this.list.splice(index,1,itemSave)
        }else{
          let max = 0;
          let newId = 0;
          for(let i = 0; i < this.list.length; i++){
            if(this.list[i].id > max){
              max = this.list[i].id
            }
          }
          newId = max + 1;
          itemSave.id = newId
          this.list.push(itemSave)
        }
        return;
    },
    clickEdit(itemEdit){
      this.hocsinh  = itemEdit
      console.log(itemEdit)
    },
    clickDelete(itemDelete){
      for(var i=0; i < this.list.length; i++){
        if(itemDelete.id === this.list[i].id){
          this.list.splice(i,1)
        }
      }
    }
  },
  data() {
    return {
      hocsinh: {

      },
      list: [
        {
          id: 1,
          name: "Vu Huy H",
          age: "22",
          phone: 54465,
          address: "HD"
        },
           {
          id: 2,
          name: "Nguyen Van A",
          age: "32",
          phone: 76576,
          address: "HN"
        },
           {
          id: 3,
          name: "Pham van B",
          age: "25",
          phone: 5654654,
          address: "HCM"
        },
           {
          id: 4,
          name: "Nguyen Dinh C",
          age: "12",
          phone: 4354,
          address: "HP"
        },
 
      ]
    }
  }
}
</script>

<style scoped>
    form{
      margin: auto;
      width: 40%;
      text-align: center;     
    }
  
    table, th, td {
      padding: 10px 20px;
      border: 1px solid;
    }
    input[type="button"] {
      display: inline-block;
      cursor: pointer;
      padding: 10 20px;
    }
</style>