<script>
	import { Swiper, SwiperSlide } from 'swiper/svelte';

	// Import Swiper styles
	import 'swiper/css';
	import "swiper/css/pagination";
	import "swiper/css/mousewheel";
	import "swiper/css/scrollbar";
	import "swiper/css/effect-fade";

	// import Swiper core and required modules
	import SwiperCore, {
	  Mousewheel, Pagination, Scrollbar, Autoplay, EffectFade, EffectCreative
	} from 'swiper';
	// install Swiper modules
	SwiperCore.use([Mousewheel, Pagination, Scrollbar, Autoplay, EffectFade, EffectCreative]);

	// 주소 복사
	import CopyClipBoard from './CopyClipBoard.svelte';

	import Toasts from "./Toasts.svelte";
	import { addToast } from "./store";

	let message = "Hello, World!";
	let types = ["success", "error", "info"];
	let type = "success";
	let dismissible = true;
	let timeout = 1200;

	let address = '';
	let e = 'clipboard';

	const copy = (v, message) => {
		address = document.getElementById(v).value;
		const app = new CopyClipBoard({
			target: document.getElementById(e),
			props: { address },
		});
		addToast({ message, type, dismissible, timeout })
		app.$destroy();
	}

	const pagination = {
	  "clickable": true,
	  "renderBullet": function (index, className) {

	          return '<span class=\"' + className + '\"><p>' + (index + 1) + '</p></span>';

	        }
	}
</script>

<main class="main">
	<style type="text/css">
		#photo_album .swiper-pagination-bullet {
			margin-left: 10px;
			margin-right: 10px;
			width: 28px;
			height: 28px;
			text-align: center;
			line-height: 20px;
			font-size: 24px;
			color: #000;
			opacity: 1;
			background: rgba(50, 50, 50, 0.2);
		}

		#photo_album .swiper-pagination-bullet-active {
		  color: #000;
		  background: rgba(255, 212, 0, 0.9);
		}

		#photo_album p {
			font-family: 'ONE-Mobile-POP';
			margin-top: 5px;
			color: #fff;
		}

		#mySwiper .swiper-pagination-bullet-active {
		  color: #000;
		  background: rgba(255, 212, 0, 0.9);
		}
	</style>
	<Toasts />
	<input id="copy_value" bind:value={address}>
	<div id="clipboard"></div>
	<input id='account1' class='acc' value="KB 91028884504">
	<input id='account2' class='acc' value="SC제일 38520100690">
	<input id='account3' class='acc' value="농협 725064-52-008793">
	<input id='account4' class='acc' value="대구은행 078-10-000262">
	<input id='account5' class='acc' value="SC제일 38520100690">
	<Swiper calculateHeight="{true}" direction="{'vertical'}" slidesPerView="{'auto'}" spaceBetween="{0}" freeMode="{true}" mousewheel="{true}" pagination='{{
		  "clickable": true,
		}}' id="mySwiper">
		<!-- <SwiperSlide>
			    <button on:click={() => addToast({ message:'주소가 복사 되었습니다.', type, dismissible, timeout })}>
			      Add toast
			    </button>
			    <div>
					
					<input id="input_test" value="서울특별시 송파구 올림픽로35다길 42 루터회관 3층 더베네치아">
					<button id="copy_address" class="btn btn-primary" on:click={ () => copy('input_test', '주소가 복사 되었습니다.') }>주소복사하기</button>
					<div id="clipboard"></div>
				</div>
		</SwiperSlide> -->
		<SwiperSlide class="first_page">
			
			<!-- <Swiper grabCursor="{true}" effect="{'creative'}" creativeEffect='{{
			  "prev": {
			    "shadow": true,
			    "translate": [
			      0,
			      0,
			      -400
			    ]
			  },
			  "next": {
			    "translate": [
			      "100%",
			      0,
			      0
			    ]
			  }
			}}' id="main_swiper"> -->
			<Swiper spaceBetween="{30}" speed="{2500}" effect="{'fade'}" navigation="{true}" autoplay='{{
				  "delay": 3000,
				  "disableOnInteraction": false
				}}' id="main_swiper" name="main_swiper">
				<SwiperSlide id="photo_1"></SwiperSlide>
				<SwiperSlide id="photo_2"></SwiperSlide>
				<SwiperSlide id="photo_3"></SwiperSlide>
			</Swiper>
			<div class="title">
				<p>유림 그리고 성진</p>
			</div>
			<div id=phrases>
				<p class="marry">결혼합니다</p>
				<p class="message">더 이상 싸우지 않고</p>
				<p class="message">잘 지낼 수 있도록</p>
				<p class="message">많은 관심과 사랑 부탁드립니다.</p>
				<p class="foot_number">2021.11.14 14:20</p>
				<p class="foot">더 베네치아</p>
				<p class="foot">잠실</p>
			</div>
		</SwiperSlide>
		<SwiperSlide class="slide_with_title">
			<div class="slide_container">
				<div class="title_space"><p>역사의 순간들</p></div>
				<Swiper id="photo_album" name="photo_album" class="mySwiper2 swiper-v" speed="{2000}" slidesPerView="{3}" spaceBetween="{-6}" pagination='{pagination}' autoplay='{{
					  "delay": 3000,
					  "disableOnInteraction": false
					}}'>
					<SwiperSlide>
						<div class="image-grid">
							<img src="img/album/1.png" alt="" class="swiper-lazy">
							<img src="img/album/2.png" alt="" class="swiper-lazy">
							<img src="img/album/3.png" alt="" class="swiper-lazy">
							<img src="img/album/4.png" alt="" class="swiper-lazy">
							<img src="img/album/5.png" alt="" class="swiper-lazy">
						</div>
					</SwiperSlide>
					<SwiperSlide>
						<div class="image-grid">
							<img src="img/album/6.png" alt="" class="swiper-lazy">
							<img src="img/album/7.png" alt="" class="swiper-lazy">
							<img src="img/album/8.png" alt="" class="swiper-lazy">
							<img src="img/album/9.png" alt="" class="swiper-lazy">
							<img src="img/album/10.png" alt="" class="swiper-lazy">
						</div>
					</SwiperSlide>
					<SwiperSlide>
						<div class="image-grid">
							<img src="img/album/11.png" alt="" class="swiper-lazy">
							<img src="img/album/12.png" alt="" class="swiper-lazy">
							<img src="img/album/13.png" alt="" class="swiper-lazy">
							<img src="img/album/14.png" alt="" class="swiper-lazy">
							<img src="img/album/15.png" alt="" class="swiper-lazy">
						</div>
					</SwiperSlide>
					<SwiperSlide>
						<div class="image-grid">
							<img src="img/album/16.png" alt="" class="swiper-lazy">
							<img src="img/album/17.png" alt="" class="swiper-lazy">
							<img src="img/album/18.png" alt="" class="swiper-lazy">
							<img src="img/album/19.png" alt="" class="swiper-lazy">
							<img src="img/album/20.png" alt="" class="swiper-lazy">
						</div>
					</SwiperSlide>
					<SwiperSlide>
						<div class="image-grid">
							<img src="img/album/21.png" alt="" class="swiper-lazy">
							<img src="img/album/22.png" alt="" class="swiper-lazy">
							<img src="img/album/23.png" alt="" class="swiper-lazy">
							<img src="img/album/24.png" alt="" class="swiper-lazy">
							<img src="img/album/25.png" alt="" class="swiper-lazy">
						</div>
					</SwiperSlide>
					<SwiperSlide>
						<div class="image-grid">
							<img src="img/album/26.png" alt="" class="swiper-lazy">
							<img src="img/album/27.png" alt="" class="swiper-lazy">
							<img src="img/album/28.png" alt="" class="swiper-lazy">
							<img src="img/album/29.png" alt="" class="swiper-lazy">
							<img src="img/album/30.png" alt="" class="swiper-lazy">
						</div>
					</SwiperSlide>
					<SwiperSlide>
						<div class="image-grid">
							<img src="img/album/31.png" alt="" class="swiper-lazy">
							<img src="img/album/32.png" alt="" class="swiper-lazy">
							<img src="img/album/33.png" alt="" class="swiper-lazy">
							<img src="img/album/34.jpg" alt="" class="swiper-lazy">
							<img src="img/album/35.png" alt="" class="swiper-lazy">
						</div>
					</SwiperSlide>
				</Swiper>
			</div>
		</SwiperSlide>
		<SwiperSlide id="map" class="slide_with_title">
			<div class="slide_container">
				<div class="title_space"><p>오시는 길</p></div>
				<img class="map_img" src="img/map.png" />
				<div class="way_to_go">
					<div><a href="https://map.daum.net/link/to/더베네치아, 37.515372444570936, 127.10297789145619" style="color:blue" target="_blank"><button class="btn btn-warning">카카오지도</button></a></div>
					<div><a href="http://map.naver.com/index.nhn?elng=127.10297789145619&elat=37.515372444570936&etext=더베네치아&menu=route&pathType=1">
						<button class="btn btn-success">네이버지도</button>
					</a></div>
					<div>
						<input id="ad" value="서울특별시 송파구 올림픽로35다길 42 루터회관 3층 더베네치아">
						<button class="btn btn-primary" on:click={ () => copy('ad', '주소가 복사 되었습니다.') }>주소복사하기</button>
					</div>
					<!-- <div>
						<button on:click={() => addToast()}>EMIT TOAST</button>
					</div> -->
				</div>
			</div>
		</SwiperSlide>
		<SwiperSlide id="contact" class="slide_with_title">
			<div class="slide_container">
				<div class="title_space"><p>마음 전하실 곳</p></div>
				<div class="grid-container">
					<div class='grid-item'>
						<div class="rows"><p class="sorry">코로나로 힘든 시기에 결혼식을</p></div>
						<div class="rows"><p class="sorry">올리게 되어 죄송스럽습니다.</p></div>
						<div class="rows"><p id="sorry_newline" class="sorry">혹시 참석하지 못하시더라도</p></div>
						<div class="rows"><p class="sorry">축복해 주시면 감사하겠습니다.</p></div>
					</div>
					<div class='grid-item'>
						<div id="cross_border1"></div>
						<div class="rows"><h1>신랑</h1></div>
						<div class="rows"><p class="name">김성진</p></div>
						<div class="rows"><button on:click={ () => copy('account1', '계좌번호가 복사 되었습니다.') }><p class="bank">KB 91028884504</p></button></div>
						<div class="rows"><a href='https://qr.kakaopay.com/281006011171148890009784'><img class='kakaopay' src='img/카카오페이_CI_combination_with_BG.svg' /></a></div>
					</div>
					<div class='grid-item'>
						<div id="cross_border2"></div>
						<div class="rows"><h1>신부</h1></div>
						<div class="rows"><p class="name">김유림</p></div>
						<div class="rows"><button on:click={ () => copy('account2', '계좌번호가 복사 되었습니다.') }><p class="bank">SC제일 38520100690</p></button></div>
						<div class="rows"><a href='https://qr.kakaopay.com/281006011000071963774752'><img class='kakaopay' src='img/카카오페이_CI_combination_with_BG.svg' /></a></div>
					</div>
					<div class='grid-item'>
						<!-- <a href='tel:01073003086'><img class='phone' src='img/phone.jpg'/></a> -->
						<div id="cross_border3"></div>
						<div class="rows"><h1>신랑측 혼주</h1></div>
						<div class="rows"><p class="name">김종훈</p></div>
						<div class="rows"><button on:click={ () => copy('account3', '계좌번호가 복사 되었습니다.') }><p class="bank">농협 725064-52-008793</p></button></div>
						<div class="rows"><p class="name">최명순</p></div>
						<div class="rows"><button on:click={ () => copy('account4', '계좌번호가 복사 되었습니다.') }><p class="bank">대구은행 078-10-000262</p></button></div>
					</div>
					<div class='grid-item'>
						<!-- <a href='tel:01073003086'><img class='phone' src='img/phone.jpg'/></a> -->
						<div id="cross_border4"></div>
						<div class="rows"><h1>신부측 혼주</h1></div>
						<div class="rows"><p class="name">김용수, 이윤희 (김유림)</p></div>
						<div class="rows"><button on:click={ () => copy('account5', '계좌번호가 복사 되었습니다.') }><p class="bank">SC제일 38520100690</p></button></div>
						<div class="rows"><p class="name"> </p></div>
						<div class="rows"><button><p class="bank">&nbsp;</p></button></div>
					</div>
				</div>
			</div>
		</SwiperSlide>
	</Swiper>
	<div role="alert" aria-live="assertive" aria-atomic="true" class="toast" data-autohide="false">
	  <div class="toast-header">
	    <img src="..." class="rounded mr-2" alt="...">
	    <strong class="mr-auto">Bootstrap</strong>
	    <small>11 mins ago</small>
	    <button type="button" class="ml-2 mb-1 close" data-dismiss="toast" aria-label="Close">
	      <span aria-hidden="true">&times;</span>
	    </button>
	  </div>
	  <div class="toast-body">
	    Hello, world! This is a toast message.
	  </div>
	</div>

	<!-- <script>

		var mapContainer = document.getElementById('map'), // 지도를 표시할 div 
		    mapOption = { 
		        center: new kakao.maps.LatLng(33.450701, 126.570667), // 지도의 중심좌표
		        level: 3 // 지도의 확대 레벨
		    };

		// 지도를 표시할 div와  지도 옵션으로  지도를 생성합니다
		var map = new kakao.maps.Map(mapContainer, mapOption);

		var markerPosition  = new kakao.maps.LatLng(33.450701, 126.570667); 

		// 마커를 생성합니다
		var marker = new kakao.maps.Marker({
		    position: markerPosition
		});

		// 마커가 지도 위에 표시되도록 설정합니다
		marker.setMap(map);

		var iwContent = '<div style="padding:5px;">예식장 <br><a href="https://map.kakao.com/link/map/Hello World!,33.450701,126.570667" style="color:blue" target="_blank">큰지도보기</a> <a href="https://map.kakao.com/link/to/Hello World!,33.450701,126.570667" style="color:blue" target="_blank">길찾기</a></div>', // 인포윈도우에 표출될 내용으로 HTML 문자열이나 document element가 가능합니다
	    iwPosition = new kakao.maps.LatLng(33.450701, 126.570667); //인포윈도우 표시 위치입니다

		// 인포윈도우를 생성합니다
		var infowindow = new kakao.maps.InfoWindow({
		    position : iwPosition, 
		    content : iwContent 
		});

		// 마커 위에 인포윈도우를 표시합니다. 두번째 파라미터인 marker를 넣어주지 않으면 지도 위에 표시됩니다
		infowindow.open(map, marker);
	</script> -->
</main>

<style>
	main {
		text-align: center;
		/*padding: 1em;*/
		max-width: 780px;
		margin: 0 auto;
		/*margin-top: 60px;*/
	}

	/*h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}*/

	/*@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}*/
</style>
