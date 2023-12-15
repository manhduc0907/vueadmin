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
                                lable="Tên Loại Sản Phẩm"
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
                    @click="addCategory"
                >Lưu</v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'AddView',
    data(){
        return{
            data:{
                TenSP: ''
            }
        }
    },
    methods:{
        addCategory(){
            axios.post('https://6541fc92f0b8287df1ff41c7.mockapi.io/products', this.data)
            .then(response =>{
                this.$emit('close');
                this.$emit('updateData');
                console.log(response.status);
            })
            .catch(error =>{
                console.log(error);     
            })
        }
    },
    props: ['dialogAdd'],
    computed:{
        dialog:{
            get(){
            return this.dialogAdd
        },
            set(value) {
                if(!value) {
                    this.$emit('close');
                }
            }
        }
    }
}
</script>

<style>

</style>