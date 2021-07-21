<template>
	<div class="wrapper " ref="wrapper1"  style="overflow: hidden;">
			<div class="content" style="min-height:100%;position: relative;z-index: 0">
				<slot></slot>
 
			</div> 

			<div  class="loading text-center" v-if="showRefresh" >
				<i class="el-icon-loading"></i>
				{{showRefresh && !refreshing?'释放刷新数据':''}}
				{{showRefresh && refreshing?'正在刷新数据':''}}

			</div>
		</div>
</template>
<script>
	import Vue from 'vue';
	import BScroll from 'better-scroll'
	import { Icon } from 'element-ui';
	Vue.use(Icon)

import '../node_modules/element-ui/lib/theme-chalk/icon.css'


	export default{
		components:{},
		props:['pageChange','refreshFun'],
		data(){
			return {
			 

				scroll:{},

				showRefresh:false, //显示下拉刷新指示
				refreshing:false,  //正在刷新数据

				touched:false
			}
		},
		methods:{

		},
		mounted(){
			if(this.scroll.refresh){
				  this.scroll.refresh();
			  }else{


				  setTimeout(()=>{
					  this.scroll = new BScroll(this.$refs.wrapper1, {
					 //  	pullUpLoad: {
						//   threshold: -20 // 在上拉到超过底部 20px 时，触发 pullingUp 事件
						// },
					  	//开启点击事件 默认为false
					  	click:true,
					  	scrollbar: {
					  	 fade: true,
					  	 interactive: false // 1.8.0 新增
					  	},
					  	mouseWheel: {
					  	 speed: 20,
					  	 invert: false,
					  	 easeTime: 300
					  	},
					  	probeType:3,
					  	bounce: true,

					  	pullDownRefresh:(()=>{

					  		if(this.refreshFun){
								return {
				                    threshold : 20,
				                    stop : 40
				                }
					  		}else{
					  			return null;
					  		}
					  	})()
					  	// pullDownRefresh : {
		      //               threshold : 30,
		      //               stop : 30
		      //           }

					    })	


					  if(this.refreshFun){


					  	 this.scroll.on('touchEnd',(pos)=>{

					   		if(this.showRefresh){

					   			if(this.refreshing){
					   				return false;
					   			}

					   			this.refreshing = true;

					   			setTimeout(()=>{

						   			this.refreshFun && this.refreshFun().then(()=>{


						   				this.showRefresh = false;
							   			this.refreshing = false;


										this.scroll.refresh();


						   			});

					   			},200)
					   		}
			            })


						this.scroll.on('scrollEnd',pos=>{


							if(this.refreshing){
					   			return false;
					   		}
							

							setTimeout(()=>{
								 

								//滚动完毕后 如果刷新的提示显示 且还没有请求刷新的接口 那就直接请求
							  	if(this.showRefresh && !this.refreshing){
							  		this.refreshing = true;

						   			// setTimeout(()=>{

							   			this.refreshFun && this.refreshFun().then(()=>{


							   				this.showRefresh = false;
								   			this.refreshing = false;


											this.scroll.refresh();


							   			});

						   			// },200)
							  	}

							},1000)



						  	
						})

					  }


					  
					  


					  // this.scroll.on('pullingUp',()=>{});
					  // this.scroll.on('pullingUp', () => {
						 // 		console.log('上拉加载');
						 //  }) 
					  let y;
					  this.scroll.on('scroll', pos=> {
					  	

					  		//配置了刷新函数 且提示没有显示
					  	if(this.refreshFun && !this.refreshing){  

						  	if(pos.y >= 20){
				                this.showRefresh = true;
				            }
					  	}


					  	// if(pos.y == y){
					  	if(pos.y < (this.scroll.maxScrollY+50)){
					  		// console.log('滚动底了');
					  		// this.getList();

							this.pageChange && this.pageChange();

					  	}else{
					  		y = pos.y;
					  	}
					  }) 



						// this.$refs.tab2.getList();


				  },400);
				  
			}
		},
		created(){
			
		},
		computed:{

		},
		watch:{

		}
	}

</script>
<style scoped>
.wrapper{
	  position:absolute; 
	  left:0;
	  top:0;
	  right:0;
	  bottom: 0;
	  /*line-height: 22px;*/
	} 
.loading{
	position: absolute;
	width: 100%;
	left:0;
	top:10px;
	text-align: center;
	font-size:12px;
	color: #666
}
</style>