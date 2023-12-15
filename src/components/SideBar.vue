<template>
  <v-navigation-drawer>
    <v-toolbar color="primary">
        <v-icon class="ml-2">mdi-home</v-icon>
        <v-toolbar-title>Quản Trị Shop</v-toolbar-title>
    </v-toolbar>
    <v-list density="compact">
      <v-list-subheader>REPORTS</v-list-subheader>

      <v-list-item
        v-for="(item, i) in links"
        :key="i"
        :value="item"
        color="primary"
      >
        <template v-slot:prepend>
          <v-icon :icon="item.icon"></v-icon>
        </template>

        <v-list-item-title>{{ item.text }}</v-list-item-title>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
    name:'SideBar',
    data(){
        return{
            links:[
                {icon:'mdi-format-list-bulleted',text:'Loại sản phẩm'},
                {icon:'mdi-sale',text:'Sản Phẩm'},
                {icon:'mdi-star-outline',text:'Đơn hàng'},
                {icon:'mdi-book-edit',text:'Chi tiết đơn hàng'},
                {icon:'mdi-account',text:'Người dùng'},
                {icon:'mdi-account-key',text:'Khách hàng'}
            ]
        }
    }
}
</script>

<style>

</style>