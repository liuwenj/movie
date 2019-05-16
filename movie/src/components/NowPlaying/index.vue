<template>
    <div class="movie_body">
        <div class="wrapper">
            <ul style="transition-duration: 0ms; transform: translate(0px, 0px) scale(1) translateZ(0px);">
                <li class="pullDown" style="pointer-events: auto;"></li>
                <li style="pointer-events: auto;">
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
                </li>
                <li style="pointer-events: auto;">
                    <div class="pic_show">
                        <img src="/image/pic2.jpg">
                    </div>
                    <div class="info_list">
                        <h2 >复仇者联盟4：终局之战
                            <img src="" alt=""></h2>
                        <p >观众评
                            <span class="grade">9.1</span></p>
                        <p >主演: 小罗伯特·唐尼,克里斯·埃文斯,马克·鲁法洛</p>
                        <p >今天207家影院放映1820场</p>
                    </div>
                    <div class="btn_mall">购票</div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  name: 'nowPlaying',
  components: {},
  data() {
    return {

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
