<template>
    <div>
    <el-table
            ref="multipleTable"
            :data="currentUser.Notes"
            style="width: 100%"
            :row-class-name="tableRowClassName"
            v-if="currentUser.Notes.length > 0"
            @selection-change="SelectionChange"
            @cell-click="onClickComplite">
        <el-table-column
                type="selection"
                width="55">
        </el-table-column>

        <el-table-column
                label="note"
                width="500">
            <template slot-scope="scope">
                <span style="margin-left: 10px" >{{scope.row.note}} </span>
            </template>
        </el-table-column>

        <el-table-column>

        </el-table-column>
        <el-table-column
                fixed="right"
                label="Operations"
                width="120">
            <template slot-scope="scope">

                <el-button
                        @click.native.prevent="deleteRow(scope.$index, currentUser.Notes)"
                        type="danger"
                        size="small">
                    <i class="el-icon-delete"></i>
                    delete
                </el-button>
            </template>
        </el-table-column>

    </el-table>

    </div>
</template>

<style>
    .el-table .success-row_my {
        background: #67C23A;
        text-decoration: line-through;
    }
</style>

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

        methods: {
            tableRowClassName({row, rowIndex}) {
                if (row.act){
                return 'success-row_my';
                }else {
                    return '';
                }

            },
            deleteRow(index, rows) {
                rows.splice(index, 1);
            },
            SelectionChange(val) {
                this.$store.dispatch('onClickCheckBox',val);

            },
            onClickComplite(row, column, cell, event) {
                row.act = !row.act;
            }

        },
    }
</script>


