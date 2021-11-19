<template>
  <div>
    <!-- <SkuForm
      :source-attribute="sourceAttribute"
      :attribute.sync="attribute"
      :sku.sync="sku"
    /> -->

    <el-row>
      <el-col :span="8">
        <div style="border:1px solid red;">
          <el-card style="border:1px solid green;">
            <el-input placeholder="请输入属性名称" v-model="attributeName">
              <template slot="append">
                <el-button icon="el-icon-plus" @click="addCard">新增属性</el-button>
              </template>
            </el-input>
          </el-card>
          <el-card v-for="(item,index) in cardList" :key="index" :header="item.header" style="border:1px solid green;">
            <el-input placeholder="请输入规格名称" v-model="item.input" style="margin-bottom: 10px;">
              <template slot="append">
                <el-button icon="el-icon-plus" @click="addAttr(index,item.input)">添加规格</el-button>
              </template>
            </el-input>
            <el-tag v-for="(item2,index2) in item.tagList" :key="index2" closable @close="tagClose(item2)" style="margin: 0 4px;">{{item2}}</el-tag>
          </el-card>
        </div>
      </el-col>
      <el-col :span="16">
        <div style="border:1px solid red;">
          <el-table :data="tableData">
            <el-table-column v-for="(item,index) in unsetTableColumnData" :key="index" :prop="item.prop" :label="item.label" align="center"></el-table-column>
            <el-table-column v-for="(item,index) in setTableColumnData" :key="index+999" :prop="item.prop" :label="item.label" align="center">
              <template slot-scope="scope">
                <!-- <span>{{scope.row}}</span> -->
                <el-input v-model="xxx"></el-input>
              </template>
            </el-table-column>
          </el-table>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
// import SkuForm from '../components/SkuForm.vue';
export default {
  // components: {SkuForm},
  data () {
    return {
      tagList: [],
      cardList: [],
      tableData: [],
      unsetTableColumnData: [],
      setTableColumnData: [
        {label: "价格",prop: "price"},
        {label: "库存",prop: "total"},
      ],
      attributeName: '',
      specName: "",
      xxx: "",
    }
  },
  
  methods: {
    // 新增属性
    addCard() {
      this.cardList.push({
        header: this.attributeName,
        tagList: [],
        input: "",
      });
      
      // this.tableData.push({
      //   price: "",
      //   total: "",
      // })

      this.unsetTableColumnData.push(
        {
          label: this.attributeName,
          prop: this.attributeName
        },
      );

      this.attributeName = "";
    },

    // 添加规格
    addAttr(index,input) {
      this.cardList[index].tagList.push(input);
      this.cardList[index].input = "";
    },

    // 删除规格
    tagClose(tag) {
      // this.cardList[index].tagList.splice(, 1);
    },
  },
};
</script>

<style scoped>

</style>
