<template>
    <div class="container">
        <div class="heading">
            <p> Private Dashboard</p> 
        </div>
        <div class="loged-in">
            <b> You are Loged In</b> <br>
            <b> Hi ...</b> 
        </div>
        <div>
            <a href="/" @click.prevent="logout()"><button>Logout</button></a>
        </div>
    </div>
    
</template>

<script>
export default {
    methods:{
        logout() {
            this.$auth.logout()
        }
    },
};

</script>


<style lang="scss" scoped>
.container {
    text-align: center;
}

.heading {
    font-size: 30px;
}

.loged-in{
    font-size: 20px;
}
    
</style>