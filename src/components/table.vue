<template>
    <div class="table">
        <table border="0" cellspacing="0">  
            <thead>
              <tr>
                  <th>Id</th>
                  <th>域名</th>
                  <th>ip</th>
                  <th>端口</th>
                  <th>适用版本</th>
                  <th>用途</th>
                  <th>操作</th>
              </tr>
            </thead>
            <tbody>
                <tr v-for="(item, index) in list" :key="index">
                  <td>{{item.Id}}</td>
                  <td>{{item.Domain}}</td>
                  <td>{{item.IP}}</td>
                  <td>{{item.Port}}</td>
                  <td>{{item.Version}}</td>
                  <td>启动上报接口</td>
                  <td>
                    <a title="配置通道"><Icon type="ios-color-filter-outline" /></a>
                    <a title="删除" ><Icon type="ios-trash" color="red"/></a>
                  </td>
                </tr>
            </tbody>
          </table> 
    </div>
</template>

<script>
export default {
    data() {
        return{
          order:''
        }
    },
    props:['list','tableColumns'],
    methods:{
    }
}
</script>

<style>
   table {
      width: 100%;
      text-align: center;
      color: #000;
      border-top: 1px solid #e8eaec;
      border-left: 1px solid #e8eaec;
      box-sizing: border-box;
      font-family: Microsoft YaHei;
      font-style: normal;
      font-weight: normal;
      font-size: 12px;
   }

   thead th{
      background-color: #f8f8f9;
      height: 30px;
      font-style: normal;
      font-weight: normal;
      font-size: 12px;
   }

   td, th {
      border-right: 1px solid #e8eaec;
      border-bottom: 1px solid #e8eaec;
   }

   td a {
     margin-right: 4px;
   }
   .button-close {
        margin-right: 5px;
        background-color: rgb(153, 153, 153);
        border-color: rgb(153, 153, 153);
        color: #fff;
   }

   button.ivu-btn {
     padding: 1px 7px 2px;
     font-size: 12px;
     box-sizing: border-box;
     width: auto;
     height: auto;
     margin: 6px 4px 6px 0;
   }
   button.normal-status {
     color: #52c41a;
   }

    .caret {
     width: 20px;
     height: 20px;
     position: relative;

   }

   .ivu-icon-md-arrow-dropdown {
     position: absolute;
     top: 4px;
     left: 0;
     font-size: 16px;
     color: #C0C4CC;
     cursor: pointer;
   }

   .ivu-icon-md-arrow-dropup {
     position: relative;
     top: -3px;
     font-size: 16px;
     color: #C0C4CC;
     cursor: pointer;
   }

   .active {
     color: #57a3f3;
   }
</style>