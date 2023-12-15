<template>
 <div>
    <v-dialog
        v-model="dialog"
        max-width="640px"
    >
        <v-card>
            <v-card-title>
                <span>Thêm mới loại sản phẩm</span>
            </v-card-title>
            <v-card-text>
                <v-form>
                    <v-container>
                        <v-row>
                            <v-col>
                                <v-text-field
                                lable="Cập nhật Loại Sản Phẩm"
                                v-model="data.TenSP"
                                ></v-text-field>
                            </v-col>
                        </v-row>
                    </v-container>
                </v-form>
            </v-card-text>
            <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                    class="mr-2"
                    color="grey darken-3"
                    @click="this.$emit('close')"
                >Hủy</v-btn>
                <v-btn
                    color="primary"
                    @click="updateCategory"
                >Cập nhật</v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    name:'EditView',
    data(){
        return{
            data:{
                id: '',
                TenSP: ''
            }
        }
    },
    methods:{
        updateCategory(){
            axios.put('https://6541fc92f0b8287df1ff41c7.mockapi.io/products'+'/'+this.data.id,this.data)
            .then(reponse =>{
                this.$emit('close');
                this.$emit('updateData');
                console.log(response.status);
            })
            .catch(error=>{
                console.log(error);
            })
        }
    },
    props: ['dialogEdit','currentItem'],
    computed:{
        dialog:{
            get(){
            return this.dialogEdit;
        },
            set(value) {
                if(!value) {
                    this.$emit('close');
                }
            }
        }
    },
    watch:{
        currentItem:function(){
            this.data.id = this.currentItem.id,
            this.data.TenSP = this.currentItem.TenSP
        }
    }    
}

</script>

<style>

</style>