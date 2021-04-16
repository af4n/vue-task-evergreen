<template>
	<header>
		<!--	Carousel	-->
		<Carousel :perPage="1" :paginationEnabled="false">
			<Slide class="first-slide"></Slide>
			<Slide class="second-slide"></Slide>
		</Carousel>
		<!--	End Carousel	-->
		<!--	Navbar	-->
		<nav>
			<div class="container">
				<div class="nav-top">
					<div class="logo">
						<span>ДОБРИВО</span>
					</div>
					<div class="info">
						<div class="info-nav">
							<ul>
								<li>
									<a href="#">Оплата и доставка</a>
								</li>
								<li>
									<a href="#">Новости</a>
								</li>
								<li>
									<a href="#">Справочник</a>
								</li>
								<li>
									<a href="#">Сертификаты</a>
								</li>
							</ul>
						</div>
						<div class="info-lang">
							<div class="lang">
								RU <span class="lang-icon"></span>
							</div>
						</div>
					</div>
				</div>
				<div class="nav-bottom">
					<div class="menu">
						<ul>
							<li>
								<a href="#">НАГРО-УДОБРЕНИЕ</a><span class="menu-icon"></span>
							</li>
							<li>
								<a href="#">БИОДИЗЕЛЬ</a><span class="menu-icon"></span>
							</li>
							<li>
								<a href="#">СИЛКО</a><span class="menu-icon"></span>
							</li>
							<li>
								<a href="#">ИНТЕРНЕТ-МАГАЗИН</a><span class="menu-icon"></span>
							</li>
							<li>
								<a href="#">ВОПРОСЫ-ОТВЕТЫ</a><span class="menu-icon"></span>
							</li>
							<li>
								<a href="#">КОНТАКТЫ</a><span class="menu-icon"></span>
							</li>
						</ul>
					</div>
					<div class="basket">
						<span class="basket-icon"></span>
						<span class="basket-text">КОРЗИНА</span>
					</div>
				</div>
			</div>
		</nav>
		<!--	End Navbar	-->
		<!-- Header Text	-->
		<div class="text">
			<div class="container">
				<h1>
					<span>ОРГАНИЧЕСКОЕ</span><br>
					<span class="text-middle">НАНО-УДОБНИЕ</span><br>
					<span class="text-last">ДОБРИВО</span>
				</h1>
			</div>
		</div>
		<!--	End Header Text	-->
	</header>
</template>

<script>
  import {Carousel, Slide} from "vue-carousel";

  export default {
    name: "Header",
    components: {
      Carousel,
      Slide
    }
  };
</script>

<style lang="scss">
	header {
		position: relative;
		
		.first-slide {
			height: 935px;
			background: url('../assets/images/carousel-bg.jpg') no-repeat center;
		}
		
		.second-slide {
			height: 935px;
			background: url('../assets/images/carousel-bg.jpg') no-repeat center;
		}
		
		nav {
			position: absolute;
			width: 100%;
			display: flex;
			justify-content: center;
			top: 190px;
			
			.container {
				
				.nav-top {
					display: flex;
					justify-content: space-between;
					align-items: center;
					
					.logo span {
						font-family: 'RobotoCondensed-Bold';
						font-size: 105px;
						color: #ffffff;
					}
					
					.info {
						display: flex;
						
						&-nav {
							display: flex;
							align-items: center;
							
							ul {
								display: flex;
								margin-bottom: 0;
								
								li a {
									font-family: 'Roboto-Light';
									font-size: 23px;
									color: #ffffff;
									margin-left: 90px;
									text-decoration: none;
								}
							}
						}
						
						&-lang {
							margin-left: 109px;
							
							.lang {
								display: flex;
								align-items: center;
								border: 2px solid #ffffff;
								padding: 8px 14px 8px 16px;
								font-size: 29px;
								color: #ffffff;
								cursor: pointer;
								
								&-icon {
									content: '';
									display: inline-block;
									width: 14px;
									height: 8px;
									background-image: url('../assets/images/arrow-down.png');
									margin-left: 12px;
								}
							}
						}
					}
				}
				
				.nav-bottom {
					display: flex;
					align-items: center;
					justify-content: space-between;
					background: #f8f8f8;
					height: 100px;
					box-shadow: 0px 3px 10px 0px #000000;
					margin-top: 20px;
					
					.menu ul {
						display: flex;
						margin-bottom: 0;
						
						li {
							display: flex;
							align-items: center;
							margin-right: 60px;
							
							a {
								font-family: 'RobotoCondensed-Bold';
								font-size: 29px;
								color: #6d6e71;
								text-decoration: none;
							}
							
							span {
								content: '';
								display: inline-block;
								width: 7px;
								height: 12px;
								background-image: url('../assets/images/arrow-right.png');
								margin-left: 20px;
							}
						}
					}
					
					.basket {
						width: 391px;
						height: 98px;
						display: flex;
						align-items: center;
						justify-content: center;
						font-family: 'RobotoCondensed-Bold';
						font-size: 29px;
						color: #ffffff;
						background-image: linear-gradient(to top, #755c1e, #796d16, #768010, #6a9415, #52a828);
						margin-top: 1px;
						margin-right: 2px;
						cursor: pointer;
						
						&:hover {
							opacity: .9;
						}
						
						&-icon {
							content: '';
							display: inline-block;
							width: 20px;
							height: 17px;
							background: url('../assets/images/basket.png') no-repeat center;
							border: 2px solid #ffffff;
							border-radius: 25px;
							padding: 20px;
							opacity: .3;
							margin-right: 17px;
						}
					}
				}
			}
		}
		
		.text {
			position: absolute;
			bottom: 20px;
			width: 100%;
			
			h1 {
				font-family: 'RobotoCondensed-Bold';
				font-size: 125px;
				line-height: 0.8;
				color: #ffffff;
				margin-left: 190px;
			}
			
			&-middle {
				margin-left: 230px;
			}
			
			&-last {
				margin-left: 360px;
			}
		}
	}
	
	@media (min-width: 1600px) {
		.container {
			max-width: 2085px;
		}
	}
	
	@media (min-width: 1200px) and (max-width: 1599px) {
		.nav-top {
			.logo span {
				font-size: 60px !important;
			}
			
			.info-nav ul li a {
				font-size: 16px !important;;
				margin-left: 50px !important;
			}
			
			.info-lang .lang {
				padding: 5px 10px !important;
				font-size: 20px !important;
			}
		}
		
		.nav-bottom {
			height: 70px !important;
			
			.menu ul li {
				margin-right: 30px !important;
				
				a {
					font-size: 14px !important;
				}
				
				span {
					margin-left: 10px !important;
				}
			}
			
			.basket {
				width: 250px !important;
				height: 68px !important;
				font-size: 20px !important;
				margin-right: 1px !important;
			}
		}
		
		.text h1 {
			font-size: 80px !important;
			line-height: 1 !important;
			margin-left: 60px !important;
			
			.text-middle {
				margin-left: 130px !important;
			}
			
			.text-last {
				margin-left: 260px !important;
			}
		}
	}
	
	@media (max-width: 1199px) {
		.nav-top {
			
			.logo span {
				font-size: 60px !important;
			}
			
			.info-nav ul li a {
				font-size: 14px !important;
				margin-left: 20px !important;
			}
		}
		
		.nav-bottom {
			height: 70px !important;
			
			.menu ul li {
				margin-right: 10px !important;
				
				a {
					font-size: 16px !important;
				}
			}
			
			.basket {
				width: 220px !important;
				height: 68px !important;
				font-size: 20px !important;
				margin-right: 1px !important;
			}
		}
		
		.text h1 {
			font-size: 80px !important;
			line-height: 1 !important;
			margin-left: 90px !important;
		}
	}
	
	@media (max-width: 991px) {
		.nav-top {
			
			.logo span {
				font-size: 40px !important;
			}
			
			.info-nav ul li a {
				margin-left: 15px !important;
			}
			
			.info-lang {
				margin-left: 10px !important;
				
				.lang {
					padding: 5px 10px !important;
					font-size: 18px !important;
					
					.lang-icon {
						margin-left: 5px !important;
					}
				}
			}
		}
		
		.nav-bottom {
			height: 50px !important;
			
			.menu ul {
				padding-left: 10px !important;
				
				li a {
					font-size: 12px !important;
				}
			}
			
			.basket {
				height: 48px !important;
				font-size: 14px !important;
				
				.basket-icon {
					padding: 15px !important;
				}
			}
		}
		
		.text h1 {
			font-size: 60px !important;
			margin-left: 50px !important;
			
			.text-middle {
				margin-left: 130px !important;
			}
			
			.text-last {
				margin-left: 260px !important;
			}
		}
	}
	
	@media (max-width: 767px) {
		.nav-top {
			flex-direction: column !important;
			
			.info-nav ul {
				padding-left: 0 !important;
				
				li a {
					margin-left: 10px !important;
					font-size: 11px !important;
				}
			}
			
			
			.lang {
				display: none !important;
			}
		}
		
		.nav-bottom {
			height: 40px !important;
			
			.menu ul {
				padding-left: 5px !important;
				
				li a {
					font-size: 8px !important;
				}
			}
			
			li span {
				width: 0 !important;
				margin-left: 0 !important;
			}
			
			.basket {
				height: 38px !important;
				width: 120px !important;
				font-size: 14px !important;
				
				&-icon {
					margin-right: 0 !important;
				}
				
				&-text {
					display: none;
				}
			}
		}
		
		.text {
			h1 {
				font-size: 40px !important;
				margin-left: 0px !important;
				
				.text-middle {
					margin-left: 60px !important;
				}
				
				.text-last {
					margin-left: 160px !important;
				}
			}
			
		}
	}
</style>