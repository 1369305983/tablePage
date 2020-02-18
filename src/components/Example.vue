<template>
   <div class="example">
      <Table :columns="historyColumns" :data="historyData"></Table>
      <Page :total="dataCount" :page-size="pageSize" show-total show-elevator show-sizer @on-change="changepage"  :page-size-opts="pageSizeOpts" ></Page>
    </div>
</template>

<script>
let testData = {
    "histories": [
        {
            "username": "智能审批",
            "shenpistatus": "审批已通过",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-24 18:11",
            "id": 1,
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批已通过",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-24 18:11",
            "id": 2,
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批已通过",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-24 10:04",
            "id": 3
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201",
            "time": "2017-07-24 10:03",
            "id": 4
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201",
            "time": "2017-07-24 10:02",
            "id": 5
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批已通过",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-24 10:02",
            "id": 6
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-24 10:01",
            "id": 7
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-24 09:56",
            "id": 8
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-21 14:23",
            "id": 9
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
            "time": "2017-07-21 14:23",
            "id": 10
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-21 14:23",
            "id": 11
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
            "time": "2017-07-21 14:23",
            "id": 12
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
            "time": "2017-07-21 14:23",
            "id": 13
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
            "time": "2017-07-21 14:21",
            "id": 14
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-21 14:21",
            "id": 15
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-21 14:20",
            "id": 16
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
            "time": "2017-07-21 14:20",
            "id": 17
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-21 14:14",
            "id": 18
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-21 14:13",
            "id": 19
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-21 14:11",
            "id": 20
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-21 14:10",
            "id": 21
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
            "time": "2017-07-20 18:09",
            "id": 22
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
            "time": "2017-07-20 18:08",
            "id": 23
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
            "time": "2017-07-20 18:08",
            "id": 24
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-20 18:07",
            "id": 25
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-20 18:05",
            "id": 26
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批已通过",
            "shenpicomments": "wedfqw",
            "time": "2017-07-20 15:50",
            "id": 27
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批已通过",
            "shenpicomments": "wedfqw",
            "time": "2017-07-20 15:20",
            "id": 28
        },
        {
            "username": "智能审批",
            "shenpistatus": "审批被拒绝",
            "shenpicomments": "自动审批通过",
            "time": "2017-07-19 18:27",
            "id":29
        }
    ]
}
export default {
    data() {
        return {
            ajaxHistoryData:[],
            // 初始化信息总条数
            dataCount:0,
            // 每页显示多少条
            pageSize:10,
            historyColumns: [
                {
                    title: 'Id号',
                    key: 'id'
                },
                {
                    title: '人员',
                    key: 'username'
                },
                {
                    title: '操作',
                    key: 'shenpistatus'
                },
                {
                    title: '意见',
                    key: 'shenpicomments'
                },
                {
                    title: '时间',
                    key: 'time'
                }

            ],
            historyData: [],
            pageSizeOpts: [5, 10, 20, 50]
        }
    },
    methods: {
        //处理历史数据
        handleListHistory() {
            this.ajaxHistoryData = testData.histories;
            this.dataCount = testData.histories.length;

            //如果dataCount<pageSize
            if(testData.histories.length < this.pageSize) {
                this.historyData = testData.histories;
            }else {
                this.historyData = testData.histories.slice(0,this.pageSize)
            }
        },
        changepage(index) {
            var _start = (index - 1) * this.pageSize;
            var _end = index * this.pageSize;
            this.historyData = this.ajaxHistoryData.slice(_start, _end);
        }
    },
    created() {
        this.handleListHistory();
    }
}
</script>

<style>

</style>