<template>
    <div class="movie_body" ref="movie_body">  
			<Loading v-if="isLoading" />
			<Scroller v-else :handleToScroll="handleToScroll" :handleToTouchEnd="handleToTouchEnd">
				<ul>
					<!-- <li class="pullDown" style="pointer-events: auto;"></li> -->
					<!-- <li style="pointer-events: auto;">
						<div class="pic_show">
							<img src="/image/pic1.jpg">
						</div>
						<div class="info_list">
							<h2 >大侦探皮卡丘
								<img src="" alt=""></h2>
							<p >观众评
								<span class="grade">8.6</span></p>
							<p >主演: 瑞安·雷诺兹,贾斯蒂斯·史密斯,凯瑟琳·纽顿</p>
							<p >今天214家影院放映3275场</p>
						</div>
						<div class="btn_mall">购票</div>
					</li> -->
					<li class="pullDown" style="pointer-events: auto;">{{pullDown}}</li>
					<li style="pointer-events: auto;" v-for="item in movieList" :key="item.id">
						<div class="pic_show" @tap="handleToDetail(item.id)">
							<img :src="item.img | setWH('128.180')">
						</div>
						<div class="info_list">
							<h2 @tap="handleToDetail(item.id)">{{item.nm}}
								<img src="" alt=""></h2>
							<p >观众评
								<span class="grade">{{item.sc}}</span></p>
							<p >主演: {{item.star}}</p>
							<p >{{item.showInfo}}</p>
						</div>
						<div class="btn_mall">购票</div>
					</li>
				</ul>
			</Scroller>
		</div>
</template>

<script>
import BScroll from 'better-scroll';
export default {
  name: 'nowPlaying',
  components: {},
  data(){
    return {
		movieList:[],
		pullDown:'',
		isLoading:true,
		prevCityId:-1
    }
	},
  activated(){
		var cityId=this.$store.state.city.id;
		if(this.prevCityId === cityId){return;}
		this.isLoading=true;
	  this.axios.get('/api/movieOnInfoList?cityId='+cityId).then((res)=>{
				console.log(1234)
		  var msg=res.data.msg;
		  if(msg === 'ok'){
				this.movieList=res.data.data.movieList;
				this.isLoading=false;
				this.prevCityId=cityId;
			  /* this.$nextTick(()=>{
				  var scroll = new BScroll(this.$refs.movie_body,{
					  tap:true,
					  probeType:1
				  });
					scroll.on('scroll',(pos)=>{
						if(pos.y > 30){
							this.pullDown ='正在更新中'
						}
					});
					scroll.on('touchEnd',(pos)=>{
						if(pos.y >30){
							this.pullDown='更新完成'
							this.axios.get('/api/movieOnInfoList?cityId=12').then((res)=>{
								if(msg === 'ok'){
									setTimeout(()=>{
										 this.movieList=res.data.data.movieList;
										 this.pullDown='';
									},1000)
								}
							})
						}
					})
			  }) */
		  }
	  })
  },
  methods:{
	  handleToDetail(movieId){
		 this.$router.push('/movie/detail/'+movieId)
		},
		handleToScroll(pos){
			if(pos.y > 30){
				this.pullDown ='正在更新中'
			}
		},
		handleToTouchEnd(pos){
			if(pos.y >30){
				this.pullDown='更新完成'
				this.axios.get('/api/movieOnInfoList?cityId=12').then((res)=>{
					var msg=res.data.msg;
					if(msg === 'ok'){
						setTimeout(()=>{
								this.movieList=res.data.data.movieList;
								this.pullDown='';
						},1000)
					}
				})
			}
		}
  }
}
</script>

<style scoped lang="stylus">
#content .movie_body {
	-webkit-box-flex: 1;
	-ms-flex: 1;
	flex: 1;
	overflow: auto
}

.movie_body ul {
	margin: 0 12px;
	overflow: hidden
}

.movie_body ul li {
	margin-top: 12px;
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	border-bottom: 1px solid #e6e6e6;
	padding-bottom: 10px
}

.movie_body .pic_show {
	width: 64px;
	height: 90px
}

.movie_body .pic_show img {
	width: 100%
}

.movie_body .info_list{
	margin-left: 10px;
	-webkit-box-flex: 1;
	-ms-flex: 1;
	flex: 1;
	position: relative
}

.movie_body .info_list h2 {
	font-size: 17px;
	line-height: 24px;
	width: 150px;
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis
}

.movie_body .info_list p {
	font-size: 13px;
	color: #666;
	line-height: 22px;
	width: 200px;
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis
}

.movie_body .info_list .grade {
	font-weight: 700;
	color: #faaf00;
	font-size: 15px
}

.movie_body .info_list img {
	width: 50px;
	position: absolute;
	right: 10px;
	top: 5px
}

.movie_body .btn_mall,.movie_body .btn_pre {
	width: 47px;
	height: 27px;
	line-height: 28px;
	text-align: center;
	background-color: #f03d37;
	color: #fff;
	border-radius: 4px;
	font-size: 12px;
	cursor: pointer
}

.movie_body .btn_pre {
	background-color: #3c9fe6
}

.movie_body .pullDown {
	margin: 0;
	padding: 0;
	border: none
}
</style>
