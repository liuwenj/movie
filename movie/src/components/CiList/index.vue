<template>
    <div class="cinema_body">
        <ul>
            <!-- <li>
                <div>
                <span>保利国际影城(天安门店)</span>
                <span class="q">
                    <span class="price">24</span>元起</span></div>
                <div class="address">
                <span>西城区煤市街廊房头条交叉口东北角北京坊东区B1-B2层</span>
                <span>600m</span></div>
                <div class="card">
                <div class="or">折扣卡</div>
                <div class="or">小吃</div></div>
            </li> -->
            <li v-for="item in cinemas" :key="item.id">
                <div>
                    <span>{{item.nm}}</span>
                    <span class="q">
                        <span class="price">{{item.sellPrice}}</span>元起
                    </span>
                </div>
                <div class="address">
                    <span>{{item.addr}}</span>
                    <span>{{item.distance}}</span>
                </div>
                <div class="card">
                    <div v-for="(num,key) in item.tag" v-if="num === 1" :key="key" :class="key | classCard">{{key | formatCard}}</div>
               </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  name: 'CiList',
  components: {},
  data() {
    return {
        cinemas:[]
    }
  },
  mounted(){
      this.axios.get('/api/cinemaList?cityId=10').then((res)=>{
          var msg=res.data.msg;
          if(msg === 'ok'){
              this.cinemas=res.data.data.cinemas;
          }
      })
  },
  filters:{
      formatCard(key){
          var card=[
              {key:'allowRefund',value:'改签'},
              {key:'sell',value:'售尽'},
              {key:'endorse',value:'退'},
              {key:'snack',value:'小吃'}
          ];
          for(var i=0;i<card.length;i++){
              if(card[i].key === key){
                  return card[i].value;
              }
          }
           return ''
      },
      classCard(key){
          var card=[
              {key:'allowRefund',value:'bl'},
              {key:'endorse',value:'bl'},
              {key:'sell ',value:'or'},
              {key:'snack',value:'or'}
          ];
          for(var i=0;i<card.length;i++){
              if(card[i].key === key){
                  return card[i].value;
              }
          }
           return ''
      }
  }
}
</script>

<style scoped lang="stylus">
    
#content .cinema_body {
	-webkit-box-flex: 1;
	-ms-flex: 1;
	flex: 1;
	overflow: auto
}

.cinema_body ul {
	padding: 20px
}

.cinema_body li{
	border-bottom: 1px solid #e6e6e6;
	margin-bottom: 20px
}

.cinema_body div{
	margin-bottom: 10px
}

.cinema_body .q{
	font-size: 11px;
	color: #f03d37
}

.cinema_body .price{
	font-size: 18px
}

.cinema_body .address{
	font-size: 13px;
	color: #666
}

.cinema_body .address span:nth-of-type(2) {
	float: right
}

.cinema_body .card{
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex
}

.cinema_body .card div{
	padding: 0 3px;
	height: 15px;
	line-height: 15px;
	border-radius: 2px;
	color: #f90;
	border: 1px solid #f90;
	font-size: 13px;
	margin-right: 5px
}

.cinema_body .card div.or{
	color: #f90;
	border: 1px solid #f90
}

.cinema_body .card div.bl{
	color: #589daf;
	border: 1px solid #589daf
}
</style>
