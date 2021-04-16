<template>
	<section>
		<div class="container">
			<!--		More		-->
			<div class="more">
				<div class="more__fertilizer-img">
					<img src="../assets/images/fertilizer.png" alt="Fertilizer">
				</div>
				<div class="more__content">
					<div class="content">
						<div class="star-group">
							<span class="star"></span><h4>ПРИРОСТ УРОЖАЯ</h4>
						</div>
						<p>в сравнении с химическим удобрением</p>
						<span class="percent">30%-250%</span>
					</div>
					<div class="content">
						<div class="star-group">
							<span class="star"></span><h4>ЭКОНОМИЯ</h4>
						</div>
						<p>химических удобрений в хозяйстве</p>
						<span class="percent">до 70%</span>
					</div>
					<div class="content">
						<div class="star-group">
							<span class="star"></span><h4>РОСТ КОРНЕВОЙ</h4>
						</div>
						<p>системы растений при использовании</p>
						<span class="percent">в 3-10 раз</span>
					</div>
				</div>
				<div class="more__find">
					<div class="text">
						<p>Хотитите <br>
							трали-вали <br>
							ла-лала?</p>
						<h3>УЗНАЙТЕ <br>
							О НАГРО БОЛЬШЕ!</h3>
					</div>
					<div class="more-btn">УЗНАТЬ БОЛЬШЕ</div>
				</div>
			</div>
			<!--		End More		-->
			<!--		Form		-->
			<div class="form">
				<form action="#">
					<h3>ПОСЧИТАЙТЕ <br> ПРИБЫЛЬ</h3>
					<p><span>ДОБРИВО</span> ЭФФЕКТИВНЕЕ ХИМИИ</p>
					<span class="line"></span>
					<div class="form-group-select">
						<label for="productivity">Выберите культуру</label>
						<div class="select">
							<p @click="isCulturesVisible = !isCulturesVisible">
								{{selected}}</p><span class="select-icon"></span>
							<div class="cultures"
									 v-if="isCulturesVisible">
								<p v-for="(culture, i) in cultures"
									 :key="i"
									 @click="select(culture)">
									{{culture.name}}
								</p>
							</div>
						</div>
					</div>
					<div class="form-group">
						<label for="productivity">Урожайность, ц/га</label>
						<input v-model.trim="productivity" type="number" class="productivity" id="productivity" placeholder="20">
					</div>
					<div class="form-group">
						<label for="price">Стоимость хим. удобрения, грн/га</label>
						<input v-model.trim="price" type="number" class="price" id="price" placeholder="3000">
					</div>
					<div class="form-group">
						<label for="area">Посевная площадь, га</label>
						<input v-model.trim="area" type="number" class="area" id="area" placeholder="10">
					</div>
					<span class="line"></span>
					<div class="form-result">
						<span class="result-text">ПРИБЫЛЬ ОТ ДОБРИВА</span>
						<span v-if="result" class="result-value">{{result}}</span>
						<span v-if="result" class="result-currency">грн</span>
					</div>
				</form>
			</div>
			<!--		End Form		-->
		</div>
	</section>
</template>

<script>
  export default {
    name: "Section",
    data() {
      return {
        cultures: [
          {name: 'Пшеница ≈ 3100 грн / т', value: 3100},
          {name: 'Кукуруза ≈ 2500 грн / т', value: 2500},
          {name: 'Подсолнечник ≈ 4400 грн / т', value: 4400},
          {name: 'Сорго ≈ 2700 грн / т', value: 2700}
        ],
        selected: 'Пшеница ≈ 3100 грн / т',
        isCulturesVisible: false,
        culture: '',
        productivity: '',
        price: '',
        area: ''
      }
    },
    computed: {
      result() {
        return Math.trunc(this.culture * this.productivity / this.price * this.area)
      }
    },
    methods: {
      select(culture) {
        if (!this.isCulturesVisible) {
          this.selected = culture.name
          this.culture = culture.value
        }
      },
      hideSelect() {
        this.isCulturesVisible = false
      }
    },
    mounted() {
      document.addEventListener('click', this.hideSelect.bind(this), true)
    },
    beforeDestroy() {
      document.removeEventListener('click', this.hideSelect)
    }
  }
</script>

<style scoped lang="scss">
	.container {
		display: flex;
		
		.more {
			position: relative;
			width: 1280px;
			
			&__fertilizer-img {
				position: absolute;
				left: 50px;
				top: -122px;
			}
			
			&__content {
				padding-left: 500px;
				padding-top: 20px;
				
				.content {
					margin-bottom: 30px;
					
					.star-group {
						display: flex;
						align-items: center;
						
						.star {
							content: '';
							display: inline-block;
							width: 70px;
							height: 67px;
							background-image: url('../assets/images/star.png');
						}
						
						h4 {
							font-family: 'RobotoCondensed-Bold';
							font-size: 52px;
							margin-left: 50px;
							margin-bottom: 0;
							color: #4d4545;
						}
					}
					
					p {
						font-size: 23px;
						color: #a7a9ac;
						margin-left: 120px;
						margin-bottom: 0;
					}
					
					.percent {
						font-size: 52px;
						color: #c49a6c;
						margin-left: 120px;
					}
				}
			}
			
			&__find {
				padding-top: 30px;
				
				.text {
					display: flex;
					
					p {
						font-family: 'Roboto-Light';
						font-size: 29px;
						text-align: end;
						margin-left: 340px;
						margin-right: 30px;
						margin-top: 0;
					}
					
					h3 {
						font-family: 'RobotoCondensed-Bold';
						font-size: 77px;
						color: #25383f;
					}
				}
				
				.more-btn {
					width: max-content;
					font-family: 'RobotoCondensed-Bold';
					font-size: 47px;
					margin-top: 30px;
					margin-bottom: 25px;
					margin-left: 540px;
					border: 10px solid #000000;
					padding: 40px 55px;
					cursor: pointer;
				}
			}
		}
		
		.form {
			position: relative;
			text-align: center;
			width: 1091px;
			background: url('../assets/images/section-bg.jpg') no-repeat top left;
			
			
			form {
				position: absolute;
				background: url('../assets/images/form-bg.jpg');
				width: 667px;
				height: 1240px;
				top: -390px;
				left: 180px;
			}
			
			h3 {
				font-family: 'RobotoCondensed-Bold';
				font-size: 75px;
				color: #25383f;
				margin-top: 60px;
				margin-bottom: 30px;
			}
			
			p {
				font-size: 29px;
				margin-bottom: 30px;
				
				span {
					font-family: 'Roboto-Medium';
				}
			}
			
			.line {
				content: '';
				display: inline-block;
				width: 358px;
				height: 2px;
				background: #d1d3d4;
			}
			
			.form-group-select {
				display: flex;
				flex-direction: column;
				margin-top: 35px;
				margin-left: 70px;
				margin-bottom: 25px;
				
				label {
					text-align: left;
					font-family: 'Roboto-Light';
					font-size: 29px;
				}
				
				.select {
					position: relative;
					width: 520px;
					height: 62px;
					display: flex;
					align-items: center;
					background-color: #fefefe;
					border: 2px solid #d1d3d4;
					padding-left: 33px;
					cursor: pointer;
					
					p {
						font-size: 29px;
						color: #a7a9ac;
						margin-bottom: 0;
					}
					
					&-icon {
						position: absolute;
						right: 18px;
						content: '';
						display: inline-block;
						width: 15px;
						height: 13px;
						background-image: url('../assets/images/select-arrow-down.png');
					}
					
					.cultures {
						position: absolute;
						width: 520px;
						top: 62px;
						left: -2px;
						background-color: #fefefe;
						border: 2px solid #d1d3d4;
						z-index: 1;
						
						p {
							height: 62px;
							display: flex;
							align-items: center;
							padding-left: 33px;
						}
					}
				}
			}
			
			.form-group {
				display: flex;
				flex-direction: column;
				margin-left: 70px;
				margin-bottom: 25px;
				
				label {
					text-align: left;
					font-family: 'Roboto-Light';
					font-size: 29px;
				}
				
				input {
					width: 520px;
					height: 62px;
					display: flex;
					align-items: center;
					background-color: #fefefe;
					border: 2px solid #d1d3d4;
					padding-left: 33px;
					font-size: 29px;
					color: #a7a9ac;
					
				}
				
				input[type="number"]::placeholder {
					color: #a7a9ac;
				}
			}
			
			.form-result {
				margin-top: 25px;
				display: flex;
				flex-direction: column;
				
				.result {
					&-text {
						font-family: 'Roboto-Light';
						font-size: 29px;
						color: #d26441;
					}
					
					&-value {
						font-family: 'RobotoCondensed-Bold';
						font-size: 97px;
						color: #d26441;
						line-height: 1;
					}
					
					&-currency {
						font-family: 'Roboto-Light';
						font-size: 29px;
						color: #25383f;
					}
				}
			}
		}
	}
	
	@media (min-width: 1200px) and (max-width: 1599px) {
		.more {
			&__fertilizer-img {
				left: -30px !important;
				
				img {
					width: 70% !important;
				}
			}
			
			&__content {
				padding-left: 300px !important;
				
				.content {
					margin-bottom: 0 !important;
					
					.star-group h4 {
						font-size: 27px !important;
						margin-left: 20px !important;
					}
					
					p {
						font-size: 11px !important;
						margin-left: 90px !important;
					}
					
					.percent {
						font-size: 27px !important;
						margin-left: 90px !important;
					}
				}
			}
			
			&__find {
				
				.text p {
					font-size: 20px !important;
					margin-left: 140px !important;
				}
				
				.text h3 {
					font-size: 50px !important;
				}
				
				.more-btn {
					font-size: 32px !important;
					margin-top: 30px;
					margin-bottom: 25px;
					margin-left: 240px !important;
					border: 6px solid #000000 !important;
					padding: 20px 25px !important;
				}
			}
		}
		
		.form form {
			background-size: 100% !important;
			width: 370px !important;
			height: 686px !important;
			top: -190px !important;
			left: 141px !important;
			
			h3 {
				font-size: 40px !important;
				line-height: 1 !important;
				margin-top: 30px !important;
				margin-bottom: 10px !important;
			}
			
			p {
				font-size: 18px !important;
				margin-bottom: 0 !important;
			}
			
			.line {
				width: 250px !important;
			}
			
			.form-group-select {
				margin-left: 40px !important;
				margin-top: 5px !important;
				margin-bottom: 10px !important;
				
				label {
					font-size: 18px !important;
					margin-bottom: 0 !important;
				}
				
				.select {
					width: 290px !important;
					height: 42px !important;
					padding-left: 13px !important;
					
					p {
						margin-bottom: 0 !important;
					}
					
					.cultures {
						width: 290px !important;
						top: 42px !important;
						
						p {
							height: 42px !important;
						}
					}
				}
			}
			
			.form-group {
				margin-left: 40px !important;
				margin-top: 15px !important;
				margin-bottom: 10px !important;
				
				label {
					font-size: 18px !important;
					margin-bottom: 0 !important;
				}
				
				input {
					width: 290px !important;
					padding-left: 13px !important;
					height: 42px !important;
					font-size: 18px !important;
				}
			}
			
			.form-result {
				margin-top: 10px !important;
				
				.result-text {
					font-size: 24px !important;
				}
				
				.result-value {
					font-size: 60px !important;
					line-height: 0.9 !important;
				}
				
				.result-currency {
					font-size: 20px !important;
				}
			}
		}
	}
	
	@media (max-width: 1199px) {
		section .container {
			display: flex !important;
			flex-direction: column !important;
		}
		
		.more {
			width: 100% !important;
			
			&__fertilizer-img {
				left: 0 !important;
			}
			
			&__content[data-v-8fbe9336] {
				padding-left: 450px !important;
			}
			
			.content {
				h4 {
					font-size: 46px !important;
				}
				
				p {
					font-size: 18px !important;
				}
				
				.percent {
					font-size: 46px !important;
				}
			}
			
			.text {
				
				p {
					width: 200px !important;
					margin-left: 240px !important;
				}
				
				h3 {
					font-size: 56px !important;
				}
			}
			
			.more-btn {
				margin-left: 370px !important;;
			}
		}
		
		.container .form {
			width: 100% !important;
			display: flex !important;
			justify-content: center !important;
			margin-top: 300px;
			
			form {
				position: relative !important;
				top: -300px !important;
				left: 0 !important;
				margin-top: 30px !important;
				margin-bottom: 30px !important;
			}
		}
	}
	
	@media (max-width: 991px) {
		.more {
			
			&__fertilizer-img {
				top: -70px !important;
				
				img {
					width: 70% !important;
				}
			}
			
			.more__content {
				padding-left: 300px !important;
				
				.content {
					h4 {
						font-size: 34px !important;
					}
					
					p {
						font-size: 14px !important;
					}
					
					.percent {
						font-size: 34px !important;
					}
				}
			}
			
			.text {
				p {
					font-size: 24px !important;
					margin-left: 140px !important;
				}
				
				h3 {
					font-size: 42px !important;
				}
			}
			
			.more-btn {
				margin-left: 200px !important;
			}
		}
	}
	
	@media (max-width: 767px) {
		.more {
			display: flex;
			flex-direction: column;
			
			&__fertilizer-img {
				position: relative !important;
				display: flex !important;
				justify-content: center !important;
				top: 30px !important;
				
				img {
					width: 50% !important;
				}
			}
			
			.more__content {
				padding-left: 0 !important;
				margin-top: 30px !important;
				
				.content {
					h4, .percent {
						font-size: 26px !important;
					}
					
					p {
						font-size: 11px !important;
					}
				}
			}
			
			.text {
				p {
					font-size: 12px !important;
					margin-left: 0 !important;
				}
				
				h3 {
					font-size: 30px !important;
				}
			}
			
			.more-btn {
				margin-left: 40px !important;
				border: 5px solid #000000 !important;
				padding: 20px 35px !important;
				font-size: 24px !important;
			}
		}
		
		.container .form {
			display: block !important;
			
			form {
				width: auto !important;
				height: 640px !important;
				background-size: contain !important;
				
				h3 {
					font-size: 26px !important;
					padding-top: 30px !important;
					margin-top: 0 !important;
					margin-bottom: 10px !important;
				}
				
				p {
					font-size: 14px !important;
					margin-bottom: 0 !important;
				}
				
				.line {
					width: 200px !important;
				}
				
				.form-group-select {
					margin-top: 10px !important;
					margin-left: 30px !important;
					margin-bottom: 10px !important;
					
					label {
						font-size: 18px !important;
						margin-bottom: 0 !important;
					}
					
					.select {
						width: 270px !important;
						height: 40px !important;
						padding-left: 20px !important;
						
						.cultures {
							width: 270px !important;
							top: 40px !important;
							
							p {
								height: 40px !important;
							}
						}
					}
				}
				
				.form-group {
					margin-top: 10px !important;
					margin-left: 30px !important;
					margin-bottom: 10px !important;
					
					label {
						font-size: 18px !important;
						margin-bottom: 0 !important;
					}
					
					input {
						width: 270px !important;
						height: 40px !important;
						padding-left: 20px !important;
						font-size: 14px !important;
					}
				}
				
				.form-result {
					margin-top: 5px !important;
					
					.result-text {
						font-size: 18px !important;
					}
					
					.result-value {
						font-size: 40px !important;
					}
					
					.result-currency {
						font-size: 18px !important;
					}
				}
			}
		}
	}

</style>
