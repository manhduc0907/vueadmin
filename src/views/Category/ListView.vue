<template>
    <div>
      <v-row class="mt-2">
      <v-icon>mdi-home</v-icon>
      <h3 class="ml-2">Danh sách loại sản phẩm</h3>
      <v-spacer></v-spacer>
      <v-btn
          icon
          size="small"
          color="#f6d365"
          @click="dialogAdd= true"
      >
          <v-icon>mdi-plus</v-icon>
      </v-btn>
    </v-row>
    <v-row>
      <v-col>
          <v-card>
              <v-table>
                  <thead>
                      <tr>
                          <th>STT</th>
                          <th>Mã loại SP</th>
                          <th>Tên loại SP</th> 
                          <th>Chức năng</th>
                      </tr>
                  </thead>
                  <tbody>
                      <tr v-for="(item,index) in categories" :key="index">
                          <td>{{ index+1 }}</td>
                          <td>{{ item.id }}</td>
                          <td>{{ item.TenSP }}</td>
                          <td>
                              <v-btn color="blue" class="mr-3" size="x-small" icon @click="dialogEdit = true,
                                                                                      currentItem= item">
                                  <v-icon>mdi-pencil</v-icon>
                              </v-btn>
                              <v-btn color="red" class="mr-3" size="x-small" icon @click="dialogDelete = true, id = item.id">
                                  <v-icon>mdi-delete</v-icon>
                              </v-btn>
                          </td>
                      </tr>
                  </tbody>
              </v-table>
          </v-card>
      </v-col>
    </v-row>
    <add-view
      :dialogAdd = "dialogAdd"
      @close="dialogAdd = false"
      @updateData = "getCategories"
    />
    <edit-view
      :dialogEdit = "dialogEdit"
      :currentItem = "currentItem"
      @close="dialogEdit = false"
      @updateData = "getCategories"
    />
    <v-dialog max-width="450px" v-model="dialogDelete">
      <v-card>
          <v-alert type="error">
              <v-row align="center">
                  <v-col cols="11" class="text-center">
                      Bạn có đồng ý xóa không
                  </v-col>
              </v-row>
              <v-row align="center">
                  <v-spacer></v-spacer>
                  <v-col cols="5">
                      <v-btn variant="text" @click="deleteCategory">Đồng ý</v-btn>
                  </v-col>
                  <v-col cols="6">
                      <v-btn variant="text" @click="dialogDelete=false">Hủy bỏ</v-btn>
                  </v-col>
              </v-row>
          </v-alert>
      </v-card>
    </v-dialog>
    </div>
  </template>
  
  <script>
  import axios from 'axios'
  import AddView from './AddView.vue'
  import EditView from './EditView.vue'
  export default {
    components: { AddView, EditView },
      name:'ListView',
      data(){
          return{
              categories:[],
              dialogAdd: false,
              dialogEdit: false,
              currentItem: '',
              dialogDelete: false,
              id:'',
          }
  },
      methods:{
          getCategories(){
              axios.get('https://6541fc92f0b8287df1ff41c7.mockapi.io/products')// ('Link api tren swagger')
              .then(response =>{
                  this.categories = response.data;
              })
              .catch(error=>{
                  console.log(error);
              })
          },
          deleteCategory(){
              axios.delete('https://6541fc92f0b8287df1ff41c7.mockapi.io/products' +'/'+ this.id)
              .then(response =>{
                  var newArr = this.categories.filter(x => x.id !=this.id);
                  this.categories = newArr;
                  this.dialogDelete = false;
                  console.log(response.status)
              })
              .catch(error=>{
                  console.log(error);
              }) 
              
          }
      },
      created(){
          this.getCategories();
      },
      
  }
  </script>
  
  <style>
  
  </style>
  