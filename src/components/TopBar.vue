<template>
  <v-app-bar color="primary">
    <v-app-bar-nav-icon></v-app-bar-nav-icon>
    <v-spacer></v-spacer>
    <v-toolbar-item>
        
        <v-btn>Hire me</v-btn>
        <v-btn>Blog</v-btn>
        <v-btn>
            <v-icon>mdi-fencing</v-icon>
        </v-btn>
        <v-btn>
            <v-badge content="999+" color="red">
                <v-icon>mdi-bell</v-icon>
            </v-badge>
        </v-btn>
        <v-btn>
            <v-avatar>
            <v-img 
                src="https://scontent.fhan14-4.fna.fbcdn.net/v/t39.30808-6/352540285_1667457463716513_1213699232460349449_n.jpg?_nc_cat=109&ccb=1-7&_nc_sid=efb6e6&_nc_ohc=uO8Yi8uEPXsAX8yuor9&_nc_ht=scontent.fhan14-4.fna&cb_e2o_trans=q&oh=00_AfBfJ3RHItmY9MbBZqs9Wl5JEv2BW4dpLvl_D3JPKfV1bw&oe=65748E22"
                alt="Duc">
                
            </v-img>
        </v-avatar>
        </v-btn>
        
    </v-toolbar-item>
  </v-app-bar>
</template>

<script>
export default {
    name:'TopBar'
}
</script>

<style>

</style>