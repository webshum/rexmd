<template>
	<div class="main-price box">
		<div class="price-video">
			<div class="inner">
				<a href="#" class="btn-video btn-popup pulse-transform" data-popup="popup-video"></a>
			</div>
		</div>

		<div class="inner">
			<h2>Lowest ED Prices...<br> <span>Guaranteed!</span></h2>

			<p><strong class="f-500">We’ve cut out the middleman</strong> so we can<br> provide the exact same meds, cheaper<br> than any competitor, or we’ll match it.</p>

			<img src="../assets/img/tablets.png" alt="" class="tablets">					

			<div class="slider-reviews">
			    <div class="slider-container">
			        <button class="prev slide-arrow" hidden="">PREV</button>			
			        <div class="track-wrap">
				        <ul class="track">
				            <li class="slide-item">
				            	<div class="head">
				            		<span>Joe B.</span>
				            		<img src="../assets/img/stars.jpeg" alt="">
				            	</div>
				            	<p>“This was my first time using telemedicine and I have to say it was simple and discreet. I would recommend this process to anyone.”</p>
				            </li>
				            <li class="slide-item">
				            	<div class="head">
				            		<span>Mark</span>
				            		<img src="../assets/img/stars.jpeg" alt="">
				            	</div>
				            	<p>"This is just what they say, the real deal! Purchased 100mg Viagra for a fraction of what I've paid before... online and from my pharmacy. My #1 choice."</p>
				            </li>
				            <li class="slide-item">
				            	<div class="head">
				            		<span>Michael G.</span>
				            		<img src="../assets/img/stars.jpeg" alt="">
				            	</div>
				            	<p>"I've attempted to use two other sites and they made it exceptionally difficult and drawn out. Your system was quick and efficient."</p>
				            </li>
				            <li class="slide-item">
				            	<div class="head">
				            		<span>Jeff W.</span>
				            		<img src="../assets/img/stars.jpeg" alt="">
				            	</div>
				            	<p>“You are doing an excellent job. Keep up the good work. Thanks to you I have a very improved relationship with my wife. Thank you so much.” </p>
				            </li>
				            <li class="slide-item">
				            	<div class="head">
				            		<span>James M.</span>
				            		<img src="../assets/img/stars.jpeg" alt="">
				            	</div>
				            	<p>“You provide an excellent product, great customer service and fast delivery. Thank you and keep up the good work.”</p>
				            </li>
				            <li class="slide-item">
				            	<div class="head">
				            		<span>Jerry</span>
				            		<img src="../assets/img/stars.jpeg" alt="">
				            	</div>
				            	<p>"This was a lot easier than I expected. Really great service, I got my medication 2 days after talking with the doctor. Thanks Rex MD!"</p>
				            </li>
				            <li class="slide-item">
				            	<div class="head">
				            		<span>Scott S.</span>
				            		<img src="../assets/img/stars.jpeg" alt="">
				            	</div>
				            	<p>“Everything was perfect. My prescription showed up on time the doctor was easy to talk to - I couldn’t be happier with the product.”</p>
				            </li>
				            <li class="slide-item">
				            	<div class="head">
				            		<span>Michael</span>
				            		<img src="../assets/img/stars.jpeg" alt="">
				            	</div>
				            	<p>"Yeah, I was pretty skeptical on this at first... but holy ****! This service is awesome."</p>
				            </li>
				        </ul>
			        </div>			
			        <button class="next slide-arrow" hidden="">NEXT</button>
			    </div>
			</div>

			<div class="hide-768">
				<h3 class="an an-top">The <span>Best Choice</span> for<br> ED Meds Online.</h3>			
				<img src="../assets/img/poste.png" alt="">
				<div class="foot">It couldn’t be any easier. Once prescribed, your<br>
				prescription is rushed direct from the pharmacy.</div>
			</div>					
		</div>
	</div>
</template>

<script>
	/* SLIDER
	------------------------------------ */
	function Slider(options) {
	    let slider = document.querySelectorAll(options.elem);

	    for (let i = 0; i < slider.length; i++) {
	        let slideContainer = slider[i].querySelector('.slider-container');
	        let track = slider[i].querySelector('.track');
	        let slideItem = slider[i].querySelectorAll('.slide-item');

	        let next = slider[i].querySelector('.next').addEventListener('click', nextSlid);
	        let prev = slider[i].querySelector('.prev').addEventListener('click', prevSlid);

	        let dots;
	        let countDot = 0;
	        let count = slideItem.length;

	        let slidesToShow = options.slidesToShow;
	        let slidesToScroll = options.slidesToScroll;
	        let responsive = options.responsive;
	        let interval = null;

	        /*  ADD-DOT 
	        ------------------------------------------------- */
	        function addDots() {
	            let slideDots = document.createElement('div');

	            for (let i = 0; i < slideItem.length / slidesToScroll; i++) {
	                slideContainer.appendChild(slideDots);
	                slideDots.classList.add('slide-dots');
	                let span = document.createElement('span');
	                slideDots.appendChild(span);
	            }

	            dots = slider[i].querySelectorAll('.slide-dots span');
	            dotsAddActive(0);
	            dotsClick();
	        }

	        /*  DOTS-CLICK 
	        ------------------------------------------------- */
	        function dotsClick() {
	            for (let i = 0; i < dots.length; i++) {
	                dots[i].onclick = function() {
	                    slideSpeed(options.speed);
	                    
	                    for (let i = 0; i < dots.length; i++) {
	                        dotsRemoveActive(i);
	                    }

	                    dotsAddActive(i);

	                    countDot = i;
	                    count = slideItem.length + i * slidesToScroll;

	                    setTransform();
	                }
	            }
	        }

	        function dotsAddActive(index) {
	            if (options.dots) dots[index].classList.add('active');
	        }

	        function dotsRemoveActive(index) {
	            if (options.dots) dots[index].classList.remove('active');
	        }

	        /*  SLIDE-CLONE
	        ------------------------------------------------- */
	        function slideClone() {
	            for (let i = 0; i < slideItem.length; i++) {
	                let cloneStart = slideItem[slideItem.length - slideItem.length + i].cloneNode(true);
	                cloneStart.classList.add('cloned');
	                track.insertBefore(cloneStart, slideItem[0]);
	            }

	            for (let i = 0; i < slideItem.length; i++) {
	                let cloneEnd = slideItem[i].cloneNode(true);
	                cloneEnd.classList.add('cloned');
	                track.appendChild(cloneEnd);
	            }
	        }

	        slideClone();

	        let slideItems = slider[i].querySelectorAll('.slide-item');

	        for (let i = 0; i < slideItems.length; i++) {
	            slideItems[i].onmousedown = function(e) {
	                e.preventDefault();
	            }
	        }
	        
	        function swipeSlider() {
	            let desc = 0;
	            let widthItem = 0;
	            let proc = 0;
	            let drob = 0;

	            /*  SWIPE DESCTOP
	            ------------------------------------------------- */
	            function swiperDesctop(e) {
	                track.addEventListener("mousedown", swipeStart);
	                let shiftX = 0;

	                function swipeStart(e) {
	                    track.removeEventListener("mousedown", swipeStart);
	                    widthItem = slideItem[0].clientWidth;
	                    proc = widthItem / 3;
	                    drob = this.clientWidth / 100;
	                    shiftX = e.pageX;

	                    track.addEventListener("mouseup", swipeEnd);
	                    track.addEventListener("mousemove", swipeMove);
	                    track.addEventListener("mouseleave", swipeEnd);

	                    setTimeout(function() {
	                        track.addEventListener("mousedown", swipeStart);
	                    }, options.speed);
	                }

	                function swipeMove(e) {
	                    slideSpeed(0);

	                    desc = e.pageX - shiftX;
	                    let swipe = count * 100 / -slidesToShow + desc / drob;
	                    track.style.transform = 'translate3d(' + swipe + '%,0,0)';
	                }

	                function swipeEnd(e) {
	                    slideSpeed(options.speed);

	                    track.style.transform = 'translate3d(' + count * 100 / -slidesToShow + '%,0,0)';

	                    if (desc < -proc) {
	                        nextSlid();
	                        desc = 0;
	                    }else if (desc > proc) {
	                        prevSlid();
	                        desc = 0;
	                    }

	                    track.removeEventListener("mousemove", swipeMove);
	                    track.removeEventListener("mouseleave", swipeEnd);
	                    track.removeEventListener("mouseup", swipeEnd);
	                };
	            }

	            swiperDesctop();

	            /*  SWIPE MOBILE
	            ------------------------------------------------- */
	            function swipeMobile() {
	                track.addEventListener("touchstart", swipeStart);
	                
	                let touchX = 0;

	                function swipeStart(e) {
	                    track.removeEventListener("touchstart", swipeStart);

	                    widthItem = slideItem[0].clientWidth;
	                    proc = widthItem / 3;
	                    drob = this.clientWidth / 100;
	                    touchX = e.changedTouches[0].screenX;

	                    track.addEventListener("touchend", swipeEnd);
	                    track.addEventListener("touchmove", swipeMove);
	                    track.addEventListener("touchleave", swipeEnd);

	                    setTimeout(function() {
	                        track.addEventListener("touchstart", swipeStart);
	                    }, options.speed);
	                }

	                function swipeMove(e) {
	                    slideSpeed(0);

	                    desc = e.changedTouches[0].screenX - touchX;
	                    let swipe = count * 100 / -slidesToShow + desc / drob;                         
	                    track.style.transform = 'translate3d(' + swipe + '%,0,0)';
	                }

	                function swipeEnd(e) {
	                    slideSpeed(options.speed);

	                    track.style.transform = 'translate3d(' + count * 100 / -slidesToShow + '%,0,0)';

	                    if (desc < -proc) {
	                        nextSlid();
	                        desc = 0;
	                    }else if (desc > proc) {
	                        prevSlid();
	                        desc = 0;
	                    }

	                    track.removeEventListener("touchmove", swipeMove);
	                    track.removeEventListener("touchleave", swipeEnd);
	                    track.removeEventListener("touchend", swipeEnd);
	                }
	            }

	            swipeMobile();
	        }        

	        function setTransform() {
	            if (responsive) {
	                const allResponsive = responsive.map(item => item.breakpoint);
	                const maxResponse = Math.max(...allResponsive);
	                const widthWindow = window.innerWidth;

	                if (widthWindow < maxResponse) {
	                    for (let i = 0; i < allResponsive.length; i++) {
	                        if (widthWindow < allResponsive[i] ) {
	                            slidesToShow = responsive[i].slidesToShow;
	                        }
	                    }
	                }else if (widthWindow > maxResponse) {
	                    slidesToShow = options.slidesToShow;
	                }
	            }

	            for (let i = 0; i < slideItems.length; i++) {
	                slideItems[i].style.minWidth = 100 / slidesToShow + '%';
	            }
	             
	            track.style.transform = 'translate3d(-' + count * 100 / slidesToShow + '%,0,0)';
	        }

	        setTransform();

	        /*  SPEED-SLIDE 
	        ------------------------------------------------- */
	        function slideSpeed(seconds) {
	            track.style.cssText = "transition: transform "+ seconds +"ms ease";                 
	        }

	        /*  CONTROL-POSITION 
	        ------------------------------------------------- */
	        function controlPosition() {
	            setTimeout(function() {
	                slideSpeed(0);
	                setTransform();
	            }, options.speed);
	        }

	        /*  BTN-DISABLED 
	        ------------------------------------------------- */
	        function btnDisabled(btn) {
	            btn.disabled = true;

	            setTimeout(function() {
	                btn.disabled = false;
	            }, options.speed, btn);
	        }
	        
	        function autoplaySlide() {
	            nextSlid();
	        }        

	        function nextSlid() {                   
	            dotsRemoveActive(countDot);
	            slideSpeed(options.speed);
	            btnDisabled(this);

	            countDot ++;
	            count = count + slidesToScroll;

	            setTransform();

	            if (count >= slideItem.length + slideItem.length) {
	                countDot = 0;
	                count = slideItem.length;

	                controlPosition();
	            }

	            dotsAddActive(countDot);
	        }

	        function prevSlid() {
	            dotsRemoveActive(countDot);
	            slideSpeed(options.speed);
	            btnDisabled(this);

	            countDot --;
	            count = count - slidesToScroll;

	            setTransform();

	            if (count < slideItem.length ) {
	                countDot = slideItem.length / slidesToScroll -1;
	                count = slideItem.length + slideItem.length - slidesToScroll;

	                controlPosition();
	            }

	            dotsAddActive(countDot);
	        }

	        function init() {
	            if (options.dots) addDots();
	            if (options.swipe) swipeSlider();
	            if (options.autoplay) {
	                interval = setInterval(autoplaySlide, options.autoplaySpeed);

	                slider[i].addEventListener('mouseover', () => {
	                    clearInterval(interval);
	                });

	                slider[i].addEventListener('mouseout', () => {
	                    interval = setInterval(autoplaySlide, options.autoplaySpeed);
	                });
	            } 

	            window.addEventListener('resize', setTransform);
	        }

	        init();
	    }
	}

	window.addEventListener('load', function() {
		new Slider({
		    elem: '.slider-reviews',
		    slidesToShow: 1,
		    slidesToScroll: 1,
		    dots: true,
		    swipe: true,
		    speed: 300,
		    autoplay: true,
		    autoplaySpeed: 3000,
		});
	});    
</script>

<style scoped>
	.main-price {
	    display: flex;
	    flex-direction: column;
	    align-items: flex-end;
	    overflow: hidden;
	}

	.main-price .inner {
	    max-width: 375px;
	    width: 100%;
	    padding: 0 20px;
	}

	.price-video {
	    width: 100%;
	    min-height: 200px;
	    background: url(../assets/img/price-video.jpg) no-repeat;
	    background-size: cover;
	    display: flex;
	    justify-content: flex-end;
	    margin-bottom: 20px;
	}
	.price-video .inner {
	    position: relative;
	}
	.price-video .btn-video {
	    display: block;
	    width: 64px;
	    height: 64px;
	    background: url(../assets/img/play.png) no-repeat;
	    position: absolute;
	    top: 50%;
	    left: 50%;
	    margin-top: -32px;
	    margin-left: -32px;
	    animation-name: pulse-transform;
	    animation-duration: 1.5s;
	    animation-iteration-count: infinite;
	    border-radius: 50%;
	    border: 2px solid transparent;
	    transition: all 0.3s;
	}
	.price-video .btn-video:hover {
	    border-color: var(--red);
	}

	.main-price h2 {
	    font-size: 33px;
	    margin-bottom: 20px;
	}

	.main-price .tablets {
	    margin: 20px auto 0 auto;
	    display: block;
	}

	.slider-reviews {
	    margin-bottom: 30px;
	}
	.slider-reviews {
	    margin-bottom: 30px;
	}
	.track {
	    display: flex;
	}
	.track-wrap {
	    overflow: hidden;
	}
	.slider-reviews .slide-item {
		display: block;
	}
	.slider-reviews .head {
	    display: flex;
	    align-items: center;
	}
	.slider-reviews .head span {
		font-size: 15px;
		font-weight: 500;
	}
	.slider-reviews .head img {
	    width: inherit;
	    margin-left: 10px;
	    position: relative;
	    top: -3px;
	}
	.slider-reviews p {
	    font-size: 15px;
	}

	.main-price h3 {
	    font-size: 26px;
	    text-align: center;
	    margin-top: 50px;
	    margin-bottom: 25px;
	}
	.main-price h3 span {
	    color: var(--red);
	}

	.main-price .foot {
	    margin-top: 40px;
    	padding-bottom: 50px;
	    text-align: center;
	    font: 15px var(--camptonBook);
	}
</style>