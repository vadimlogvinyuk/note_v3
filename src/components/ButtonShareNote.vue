<template>
    <div>
        <div class="btn-group" v-if=" Users.length >1 && multipleSelection.length > 0">
            <button type="button" class="btn btn-link dropdown-toggle" data-toggle="dropdown"
                    aria-haspopup="true" aria-expanded="false" icon="el-icon-share">
                <i class="el-icon-share"></i>
                share
            </button>
            <div class="dropdown-menu">
                <a class="dropdown-item" href="#" v-for="user in Users"
                @click="OtherUser(user)"
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
            },
            multipleSelection() {
                return this.$store.getters.multipleSelection;
            }
        },
        methods:{
            OtherUser(UserChoise) {
                this.$store.dispatch('onClickShareNotes',UserChoise);
            }
        }
    }

</script>

