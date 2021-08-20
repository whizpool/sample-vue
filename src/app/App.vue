<template>
        <div class="container " style="height:100vh">
            <div class="row d-flex w-100 h-100 align-items-center">
                
                <div class="col-sm-5 offset-sm-3 p-5 bg-white rounded">
                     <div class="brand-logo mb-2">
                    <img src="https://image.pngaaa.com/364/185364-middle.png" style="width:150px;">
                </div>  
                    <div v-if="alert.message" :class="`alert ${alert.type}`">{{alert.message}}</div>
                    <router-view></router-view>
                </div>
            </div>
        </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
    name: 'app',
    computed: {
        ...mapState({
            alert: state => state.alert
        })
    },
    methods: {
        ...mapActions({
            clearAlert: 'alert/clear' 
        })
    },
    watch: {
        $route (to, from){
            // clear alert on location change
            this.clearAlert();
        }
    } 
};
</script>