<template>
  <div class="city_body">
		<div class="city_list">
			<div class="city_hot">
				<h2>热门城市</h2>
				<ul class="clearfix">
					<li v-for="item in hotList" :key="item.id">{{item.nm}}</li>
				</ul>
			</div>
			<div class="city_sort" ref="city_sort">
				<div v-for="item in cityList" :key="item.index">
					<h2>{{item.index}}</h2>
					<ul>
						<li v-for="itemList in item.list" :key="itemList.id">{{itemList.nm}}</li>
					</ul>  
				</div>
			</div>
		</div>
		<div class="city_index">
			<ul>
				<li v-for="(item,index) in cityList" :key="item.index" @touchstart="handToIndex(index)">{{item.index}}</li>
			</ul>
		</div>
	</div>
</template>

<script>
export default {
	name: 'City',
	data(){
		return{
			cityList:[],
			hotList:[]
		}
	},
	mounted(){
		this.axios.get('/api/cityList').then((res)=>{
			if(res.data.msg==='ok'){
				var cities=res.data.data.cities;
				//[{index:'A',list:[{nm:nm,id:id}]}]
				var { hotList, cityList } =	this.formatCityList(cities);
				this.hotList=hotList;
				this.cityList=cityList;
			}
		})
	},
	methods:{
		formatCityList(cities){
				var hotList=[];
				var cityList=[];
				for(var i=0;i<cities.length;i++){
					if(cities[i].isHot ===1){
						hotList.push(cities[i])
					}
					var firstLetter=cities[i].py.substring(0,1).toUpperCase();
					if(toCom(firstLetter)){//新添加
						cityList.push
						(
								{ 
									index:firstLetter,
								    list:[{nm:cities[i].nm,id:cities[i].id}]
								}
						)
					}
					else{//累积
						for(var j=0;j<cityList.length;j++){
							if(cityList[j].index === firstLetter ){
								cityList[j].list.push({nm:cities[i].nm,id:cities[i].id})
							}
						}
					}
				}
				cityList.sort((a,b)=>{
					if(a.index > b.index){
						return 1
					}
					else if(a.index < b.index){
						return -1
					}
					else{
						return 0
					}
				})
				function toCom(firstLetter){
					for(var i=0;i<cityList.length;i++){
						if(cityList[i].index === firstLetter){
							return false
						}
					}
					return true
				}
				console.log(cityList)
			return {hotList,cityList}
		},
		handToIndex(index){
			var h2=this.$refs.city_sort.getElementsByTagName('h2');
			this.$refs.city_sort.parentNode.scrollTop=h2[index].offsetTop
		}
	}
}
</script>

<style scoped lang="stylus">
.city_body {
    margin-top: 45px;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    width: 100% ;
    position: absolute;
    top: 0;
    bottom: 0
}
.city_body .city_list { -webkit-box-flex: 1; -ms-flex: 1;
    flex: 1;
    overflow: auto;
    background: #fff5f0
}
.city_body .city_list::-webkit-scrollbar {
    background-color: transparent;
    width: 0
}
.city_body .city_hot {
    margin-top: 20px
}
.city_body .city_hot h2 {
    padding-left: 15px;
    line-height: 30px;
    font-size: 14px;
    background: #f0f0f0;
    font-weight: 400
}
.city_body .city_hot ul li {
    float: left;
    background: #fff;
    width: 29% ;
    height: 33px;
    margin-top: 15px;
    margin-left: 3% ;
    padding: 0 4px;
    border: 1px solid#e6e6e6;
    border-radius: 3px;
    line-height: 33px;
    text-align: center; 
		-webkit-box-sizing: border-box;
    box-sizing: border-box
}
.city_body .city_sort div {
    margin-top: 20px
}
.city_body .city_sort h2 {
    padding-left: 15px;
    line-height: 30px;
    font-size: 14px;
    background: #f0f0f0;
    font-weight: 400
}
.city_body .city_sort ul {
    padding-left: 10px;
    margin-top: 10px
}
.city_body .city_sort ul li {
    line-height: 30px
}
.city_body .city_index {
    width: 20px;
    display: -webkit - box;
    display: -ms - flexbox;
    display: flex; -webkit-box-orient: vertical; -webkit-box-direction: normal; -ms-flex-direction: column;
    flex-direction: column; -webkit-box-pack: center; -ms-flex-pack: center;
    justify-content: center;
    text-align: center;
    border-left: 1px solid #e6e6e6
}
</style>
