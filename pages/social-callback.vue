<template>
    <div class="container">
        <div class="heading">
            <p> Social Login</p> 
        </div>
        <div class="loged-in">
            <b> You are Loged In</b> 
        </div>
        <!-- <p>User name: {{name}}</p> -->
        <p>User token: {{token}}</p>
        <div>
            <a href="/"><button>Logout</button></a>
        </div>
    </div>
    
</template>

<script>
export default {
    methods:{

    },

    data() {
        return {
            token: this.$route.query.token ? this.$route.query.token : null,
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