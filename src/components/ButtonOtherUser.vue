<template>
    <div v-if="Users.length > 0">
        <div class="btn-group">
            <button type="button" class="btn btn-success dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                {{currentUser.userName}}
            </button>
            <div class="dropdown-menu">
                <a class="dropdown-item" href="#" v-for="user in Users" @click="OtherUser(user)"
                v-if="user != currentUser">{{user.userName}}</a>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        computed:{
            Users(){
                return this.$store.getters.Users;
            },
            currentUser() {
                return this.$store.getters.currentUser;
            }
        },
        methods:{
            OtherUser(UserChoise) {
                this.$store.dispatch('OtherUser',UserChoise);
            }
        }
    }

</script>


