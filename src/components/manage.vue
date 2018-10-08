<template>
	<div class="manage">
	
		<el-row class="inputs">
		  <el-col :span="8"><div class="grid-content bg-purple">
		  	<div class="demo-input-suffix">
			  关键字&nbsp;&nbsp;
			  <el-input
			    placeholder="请输入商品名称"
			    v-model="input21"
			    class="input1">
			  </el-input>
			</div>
		  </div></el-col>
		  <el-col :span="8"><div class="grid-content bg-purple-light">
		  	商品分类&nbsp;&nbsp;
		  	<el-select v-model="value8" filterable placeholder="请选择分类">
			    <el-option
			      v-for="item in options"
			      :key="item.value"
			      :label="item.label"
			      :value="item.value"
			      class="select1">
			    </el-option>
  			</el-select>
		  </div></el-col>
		  <el-col :span="8"><div class="grid-content bg-purple">
		  	<el-button icon="el-icon-search" class="btn-icon"></el-button>
		  </div></el-col>
		</el-row>
		
		
		<el-row class="btn">
		  <el-button class="btn-delete">删除</el-button>
		  <el-button class="btn-add">添加</el-button>
		</el-row>
				
		
	    <el-table
	      ref="multipleTable"
		    :data="tableData"
		    tooltip-effect="dark"
		    style="width: 100%">
		    <el-table-column
		      type="selection"
		      width="55">
		    </el-table-column>
	      	<el-table-column
		      prop="id"
		      label="ID"
		      width="180"
		      text-align="center">
		  	</el-table-column>
		  	<el-table-column
	        prop="sort"
	        label="商品分类">
	      	</el-table-column>
	      	<el-table-column
	        prop="name"
	        label="商品名称">
	      	</el-table-column>
	      	<el-table-column
	        prop="price"
	        label="价格">
	      	</el-table-column>
	      	<el-table-column
	        prop="date"
	        label="上传时间">
	      	</el-table-column>
	      	<el-table-column
	        prop="status"
	        label="发布状态">
	      	</el-table-column>
	      	<el-table-column label="操作">
		      	<template slot-scope="scope">
		        	<el-button
		          	size="mini"
		          	@click="handleEdit(scope.$index, scope.row)">编辑</el-button>
		        	<el-button @click.native.prevent="deleteRow(scope.$index, tableData)"
		          type="text" size="small">移除</el-button>
		      	</template>
		    </el-table-column>
	    </el-table>
    </div>
  </template>
  <script>
  	export default{
  		data(){
  			return{
  				input21: '',
  				input10: '',
  				tableData:[{
  					checked:'false',
  					id:'001',
  					sort:'美食',
  					name:'舌尖上的中国第一季',
  					price:'￥79',
  					date:'20121204',
  					status:'已发布'	
  				},
  				{	
  					checked:'false',
					id:"002",
					sort:"美食",
					name:"舌尖上的中国第二季",
					price:179,
					date:20141204,
					status:"待修改"
					
				},
				{
					checked:'false',
					id:"003",
					sort:"美食",
					name:"舌尖上的中国第三季",
					price:109,
					date:20161204,
					status:"待修改"
					
				},
				{
					checked:'false',
					id:"004",
					sort:"历史",
					name:"诸葛亮骂王朗",
					price:2999,
					date:20180201,
					status:"待修改"
					
				},
				{
					checked:'false',
					id:"005",
					sort:"新闻",
					name:"新时代特色中国梦",
					price:19,
					date:20180512,
					status:"待修改"
					
				},
				{
					checked:'false',
					id:"006",
					sort:"新闻",
					name:"新时代特色中国梦",
					price:998,
					date:20180514,
					status:"待修改"
					
				},
				{
					checked:'false',
					id:"007",
					sort:"体育",
					name:"皇马大战利物浦",
					price:369,
					date:20180515,
					status:"待修改"
					
				}
  				],
  				options: [{
			          value: '选项1',
			          label: '美食'
			        },
			        {
			          value: '选项2',
			          label: '新闻'
			        },
			        {
			          value: '选项3',
			          label: '八卦'
			        },
			        {
			          value: '选项4',
			          label: '体育'
			        },
			        {
			          value: '选项5',
			          label: '音乐'
			        }],
  				 multipleSelection: [],
  				 value8: ''
  			}
  		},
  		 methods: {
	      toggleSelection(rows) {
	        if (rows) {
	          rows.forEach(row => {
	            this.$refs.multipleTable.toggleRowSelection(row);
	          });
	        } else {
	          this.$refs.multipleTable.clearSelection();
	        }
	      },
	      handleSelectionChange(val) {
	        this.multipleSelection = val;
	      }
	    },
	     methods: {
      deleteRow(index, rows) {
        rows.splice(index, 1);
      }
    },
     
  }
  </script>
 <style>
 	.manage{width:1380px;padding: 19px;border: 1px solid #fff;}
 	.inputs{padding: 20px 0 30px 0;border-bottom: 1px solid #ccc;}
 	.btn{float:left;padding: 15px 0;}
	.btn-delete,.btn-add{width: 100px;height:50px;background: #42B983;color: #fff;font-size: 16px;}
	.cell{text-align: center;}
	.input1{width:250px;}
	.select1{width: 250px;}
	.btn-icon{float: left;background:#42B983;color: #fff;font-weight:blod;font-size:20px;}
	.el-table{border: 1px solid #ccc;border-collapse: collapse;}
	th{font-size: 16px;color: #333;}
	th,td{border: 1px solid #ccc;}

	
</style>