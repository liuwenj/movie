<template>
    <div class="cinema_body">
        <ul>
            <li>
                <div>
                <span>保利国际影城(天安门店)</span>
                <span class="q">
                    <span class="price">24</span>元起</span></div>
                <div class="address">
                <span>西城区煤市街廊房头条交叉口东北角北京坊东区B1-B2层</span>
                <span>600m</span></div>
                <div class="card">
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <div class="or">折扣卡</div>
                <div class="or">小吃</div></div>
            </li>
            <li>
                <div>
                <span>大观楼电影院</span>
                <span class="q">
                    <span class="price">34</span>元起</span></div>
                <div class="address">
                <span>西城区前门大街大栅栏街36号</span>
                <span>900m</span></div>
                <div class="card">
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <div class="or">折扣卡</div>
                <div class="or">小吃</div>
                <!----></div>
            </li>
            <li>
                <div>
                <span>耀莱成龙影城(王府井店)</span>
                <span class="q">
                    <span class="price">39</span>元起</span></div>
                <div class="address">
                <span>东城区王府井大街301号新燕莎金街购物广场地下1层MB124</span>
                <span>1.2km</span></div>
                <div class="card">
                <!---->
                <!---->
                <!---->
                <!---->
                <div class="bl">退</div>
                <!---->
                <div class="or">折扣卡</div>
                <div class="or">小吃</div>
                <!----></div>
            </li>
            <li>
                <div>
                <span>传奇奢华影城</span>
                <span class="q">
                    <span class="price">42</span>元起</span></div>
                <div class="address">
                <span>东城区东打磨厂街7号新活馆B1层</span>
                <span>1.3km</span></div>
                <div class="card">
                <div class="bl">改签</div>
                <!---->
                <!---->
                <!---->
                <div class="bl">退</div>
                <!---->
                <div class="or">折扣卡</div>
                <div class="or">小吃</div>
                <!----></div>
            </li>
            <li>
                <div>
                <span>横店电影城(王府井店)</span>
                <span class="q">
                    <span class="price">29</span>元起</span></div>
                <div class="address">
                <span>东城区王府井大街255号北京市百货大楼北馆8层</span>
                <span>1.5km</span></div>
                <div class="card">
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <div class="or">折扣卡</div>
                <div class="or">小吃</div>
                <!----></div>
            </li>
            <li>
                <div>
                <span>百老汇影城(apm购物中心店)</span>
                <span class="q">
                    <span class="price">30</span>元起</span></div>
                <div class="address">
                <span>东城区王府井大街138号北京apm6层</span>
                <span>1.6km</span></div>
                <div class="card">
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <div class="or">折扣卡</div>
                <div class="or">小吃</div></div>
            </li>
            <li>
                <div>
                <span>百老汇影城(东方广场店)</span>
                <span class="q">
                    <span class="price">30</span>元起</span></div>
                <div class="address">
                <span>东城区东长安街1号东方广场地下1层</span>
                <span>1.7km</span></div>
                <div class="card">
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <!---->
                <div class="or">折扣卡</div>
                <div class="or">小吃</div></div>
            </li>
            <li>
                <div>
                <span>搜秀影城</span>
                <span class="q">
                    <span class="price">29</span>元起</span></div>
                <div class="address">
                <span>东城区崇外大街40号搜秀城9层</span>
                <span>1.9km</span></div>
                <div class="card">
                <div class="bl">改签</div>
                <!---->
                <!---->
                <!---->
                <div class="bl">退</div>
                <!---->
                <div class="or">折扣卡</div>
                <div class="or">小吃</div>
                <!----></div>
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
