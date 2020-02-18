<template>
    <div class="table">
        <table border="0" cellspacing="0">  
            <thead>
              <tr>
                <th v-for="(item,index) in tableColumns" :key="index" @click="sortChange({prop:item.key},index)">{{item.title}}<span v-if="item.sortable" class="caret">
                  <Icon type="md-arrow-dropup" :class="[{'active':item.sortIcon == 'top'}]" />
                  <Icon type="md-arrow-dropdown"  :class="[{'active':item.sortIcon == 'bottom'}]"/></span>
                </th>
              </tr> 
            </thead>
            <!-- <tbody>
              <tr v-for="item in list">
                <td v-for="child in tableColumns">
                  <div v-if="child.key in item">{{item[child.key]}}</div>
                  <div v-else-if="child.key == 'action'">
                    <Button type="primary" v-if="child.buttonEdit" @click="Edit()">编辑</Button>
                    <Button type="primary" v-if="child.buttonUpdate">修改权限</Button>
                    <Button class="button-close" v-if="child.buttonclose" @click="Close()">关闭</Button>
                    <Button type="error" v-if="child.buttonDelete">删除</Button>
                    <a title="编辑" v-if="child.iconEdit"><Icon type="ios-create" /></a>
                    <a title="配置屏蔽规则" v-if="child.iconSet"><Icon type="ios-settings" /></a>
                    <a title="配置通道" v-if="child.iconChannel"><Icon type="ios-color-filter-outline" /></a>
                    <a title="删除" v-if="child.iconDelete"><Icon type="ios-trash" color="red"/></a>
                  </div>
                </td>
              </tr>
              <tr v-if="list.length==0"><td :colspan="tableColumns.length" style="height:38px;">暂无数据</td></tr>
            </tbody> -->
            <tbody>
                <tr v-for="(item, index) in list" :key="index">
                  <td>{{item.name}}</td>
                  <td>{{item.age}}</td>
                  <td></td>
                  <td>
                    <a title="配置通道"><Icon type="ios-color-filter-outline" /></a>
                    <a title="删除" ><Icon type="ios-trash" color="red"/></a>
                  </td>
                  <td>{{item.address}}</td>
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
      sortChange(data,index) {
        let that = this;
        const { prop } = data;
        this.tableColumns.forEach(item=>{
          item.sortIcon = "";
        })
        this.order = !this.order;
        if (this.order == true) {
          this.sortArr(that.list,prop);
          this.tableColumns[index].sortIcon = "top";
        }else if(this.order == false){
          this.sortDesArr(that.list,prop);
          this.tableColumns[index].sortIcon = "bottom"
        }
        console.log(this.tableColumns)
      },
      sortArr(arr, index) {
        console.log(arr);
        const isChineseReg = new RegExp('[\\u4E00-\\u9FFF]+', 'g');
        if (arr.length <= 1) return;
        const firstNotNullValue = this.getFirstNotNullValue(arr, index);
        if (!firstNotNullValue && firstNotNullValue !== 0) return;
        if (!isChineseReg.test(firstNotNullValue)) {
          if (isNaN(Number(firstNotNullValue))) {
            // 非中文非数值
            arr.sort();
          } else {
            // 数值型
            arr.sort((a, b) => {
              return a[index] - b[index];
            });
          }
        } else {
          arr.sort((a, b) => {
            return a[index].localeCompare(b[index], 'zh');
          });
        }
      },
    // 倒序
    sortDesArr(arr, index){
      console.log(arr);
      const isChineseReg = new RegExp('[\\u4E00-\\u9FFF]+', 'g');
      if (arr.length <= 1) return;
      const firstNotNullValue = this.getFirstNotNullValue(arr, index);
      if (!firstNotNullValue && firstNotNullValue !== 0) return;
      if (!isChineseReg.test(firstNotNullValue)) {
        if (isNaN(Number(firstNotNullValue))) {
          // 非中文非数值
          arr.sort().reverse();
        } else {
          // 数值型
          arr.sort((a, b) => {
            return b[index] - a[index];
          });
        }
      } else {
        arr.sort((a, b) => {
          return b[index].localeCompare(a[index], 'zh');
        });
      }
    },
    getFirstNotNullValue (array, index) {
        if (!(array && array.length)) return false;
        let r = -1;
        let rowLength = array.length;
        while (++r < rowLength) {
          let item = array[r][index];
          if (item || item === 0) return item;
        }
        return false;
      },
      Edit() {
        this.$emit('editData');
      },
      Close() {
        this.$emit('closeData');
      }
    },
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