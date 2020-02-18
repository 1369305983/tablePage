<template>
    <div class="table">
        <formTable :tableColumns="tableColumns" :list="list"  @editData="editData" @closeData="closeData"></formTable>
         <Page :current="currentPage"  :total="TotalCnt" show-total show-elevator show-sizer @on-page-size-change="onPageSizeChage" @on-change="onChangePage" placement="top" :page-size="pageSize" :page-size-opts="pageSizeOpts"></Page>
    </div>
</template>

<script>
    import formTable from './table.vue'
    export default {
        data () {
            return {
                tableColumns: [
                    {
                        title: 'Name',
                        key: 'name',
                        sortable:true,
                        sortIcon:''
                    },
                    {
                        title: 'Age',
                        key: 'age',
                        sortable:true,
                        sortIcon:''
                    },{
                        title:'状态',
                        key:'status'
                    },
                    {
                        title: 'Action',
                        key:'action',
                        width: 150,
                        buttonEdit: true,
                        buttonUpdate: true,
                        buttonClose: true,
                        buttonDelete: true,
                        iconEdit:true,
                        iconDelete:true
                        // children:{
                        //     button:[{
                        //         name:'编辑',
                        //         type:'primary',
                        //         class:''
                        //     },
                        //     {
                        //         name:'修改权限',
                        //         type:'primary',
                        //         class:''
                        //     },
                        //     {
                        //         name:'关闭',
                        //         type:'',
                        //         class:'button-close'
                        //     },
                        //     {
                        //         name:'删除',
                        //         type:'error',
                        //         class:''
                        //     }],
                        //     icon:[{
                        //         name:'编辑',
                        //         icon:'ios-create',
                        //         color:''
                        //     },
                        //     {
                        //         name:'配置屏蔽规则',
                        //         icon:'ios-settings',
                        //         color:''
                        //     },
                        //     {
                        //         // name:'配置通道',
                        //         // icon:'ios-color-filter-outline',
                        //         // color: ''
                        //     },{
                        //         name:'删除',
                        //         icon:'ios-trash',
                        //         color:'red'
                        //     }]
                        // }
                        // children:{
                        //     button:[],
                        //     icon:[]
                        // }
                    },
                    {
                        title: 'Address',
                        key: 'address'
                    }
                ],
                // list: [
                //     {
                //         name: '',
                //         age: 18,
                //         address: 'New York No. 1 Lake Park'
                //     },
                //     {
                //         name: 'Jim Green',
                //         age: 24,
                //         address: 'London No. 1 Lake Park'
                //     },
                //     {
                //         name: 'Joe Black',
                //         age: 30,
                //         address: 'Sydney No. 1 Lake Park'
                //     },
                //     {
                //         name: 'Jon Snow',
                //         age: 26,
                //         address: 'Ottawa No. 2 Lake Park'
                //     }
                // ]
                // list:[{"Id":6,"UserName":"zw","CompanyName":"12","LinkName":"zw","LinkTel":"18813902206","Status":1,"CreateTime":1575352421,"CreateId":103,"ModId":1575353324,"ModTime":103},{"Id":4,"UserName":"liubankeji","CompanyName":"深圳市六瓣科技有限公司","LinkName":"毕伟","LinkTel":"","Status":1,"CreateTime":1571711352,"CreateId":105,"ModId":0,"ModTime":0},{"Id":3,"UserName":"junhua","CompanyName":"huangjunhua","LinkName":"黄俊华","LinkTel":"","Status":1,"CreateTime":1571366973,"CreateId":105,"ModId":1574320660,"ModTime":105},{"Id":2,"UserName":"HSX123","CompanyName":"","LinkName":"旭","LinkTel":"","Status":1,"CreateTime":1571127477,"CreateId":50,"ModId":0,"ModTime":0},{"Id":1,"UserName":"lingdu","CompanyName":"lingdu","LinkName":"测试","LinkTel":"","Status":1,"CreateTime":1571043936,"CreateId":105,"ModId":1571105354,"ModTime":105}],
                // TotalCnt:5,
                list:[{"Id":8,"Domain":"http://w06k0a.iw78w8.com:12038/","IP":"127.0.0.1","Port":12038,"UseType":4,"Version":3000},{"Id":7,"Domain":"http://w06k0a.iw78w8.com:12038/","IP":"127.0.0.1","Port":12038,"UseType":3,"Version":3000},{"Id":6,"Domain":"http://w06k0a.iw78w8.com:12038/","IP":"127.0.0.1","Port":12038,"UseType":2,"Version":3000},{"Id":5,"Domain":"http://w06k0a.iw78w8.com:12038/","IP":"127.0.0.1","Port":12038,"UseType":1,"Version":3000},{"Id":4,"Domain":"http://ks7br7.3q03on.com:12038/","IP":"127.0.0.1","Port":12038,"UseType":4,"Version":3000},{"Id":3,"Domain":"http://ks7br7.3q03on.com:12038/","IP":"127.0.0.1","Port":12038,"UseType":3,"Version":3000},{"Id":2,"Domain":"http://ks7br7.3q03on.com:12038/","IP":"127.0.0.1","Port":12038,"UseType":2,"Version":3000},{"Id":1,"Domain":"http://ks7br7.3q03on.com:12038/","IP":"127.0.0.1","Port":12038,"UseType":1,"Version":3000}],
                TotalCnt:8,
                currentPage:1,
                pageSize:50,
                pageSizeOpts:[5,10,15,30,50,100],
            }
        },
        components:{
            formTable
        },
        methods: {
            closeData() {
                console.log('close')
            },
            editData() {
                console.log('edit')
            },
            onChangePage(newPage){
                // this.currentPage = newPage;
                // this.reloadData();
                console.log('change')
            },
            onPageSizeChage(newPageSize){
                // this.pageSize = newPageSize;
                // let offset = (this.currentPage - 1) * this.pageSize;
                // if(offset>this.totalCnt){
                //     this.currentPage = 1;
                // }else{
                //     this.reloadData();
                // }
                console.log(newPageSize)
            },
            reloadData(){
                this.$emit("submit",this.currentPage,this.pageSize);
            },
        }
    }
</script>

<style>
</style>