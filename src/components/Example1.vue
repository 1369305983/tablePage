<template>
    <div class="example">
        <Table border :columns="columns6" :data="data5"></Table>
        <Page  :total="TotalCnt" show-total show-elevator show-sizer @on-change="changepage" @on-page-size-change="pages"  :page-size="pageSize" :page-size-opts="pageSizeOpts"></Page>
    </div>
</template>
<script>
    export default {
        data () {
            return {
                columns6: [
                    {
                        title: 'Date',
                        key: 'date'
                    },
                    {
                        title: 'Name',
                        key: 'name'
                    },
                    {
                        title: 'Age',
                        key: 'age',
                        filters: [
                            {
                                label: 'Greater than 25',
                                value: 1
                            },
                            {
                                label: 'Less than 25',
                                value: 2
                            }
                        ],
                        filterMultiple: false,
                        filterMethod (value, row) {
                            if (value === 1) {
                                return row.age > 25;
                            } else if (value === 2) {
                                return row.age < 25;
                            }
                        }
                    },
                    {
                        title: 'Address',
                        key: 'address',
                        filters: [
                            {
                                label: 'New York',
                                value: 'New York'
                            },
                            {
                                label: 'London',
                                value: 'London'
                            },
                            {
                                label: 'Sydney',
                                value: 'Sydney'
                            }
                        ],
                        filterMethod (value, row) {
                            return row.address.indexOf(value) > -1;
                        }
                    }
                ],
                data5: [
                    {
                        name: 'John Brown',
                        age: 18,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: 'Jim Green',
                        age: 24,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 30,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    },
                    {
                        name: 'Jimen',
                        age: 24,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joeck',
                        age:56,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Snow',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    }
                ],
                TotalCnt:7,
                currentPage:1,
                pageSize:50,
                pageSizeOpts:[5,10,15,30,50,100],
            }
        },
        methods: {
            pages(num) { //修改每页显示条数时调用
                console.log(num)
                this.pageSize = num;
                this.changepage(num);
            },
            changepage(index) {
                console.log('change')
            }
        }
    }
</script>