<template>
  <div class="carousel">
    <div class="carousel__item carousel__item--visible">
      <img src="../assets/imgs/one.jpg" alt="" class="carousel__img">
    </div>
    <div class="carousel__item carousel__item--hidden">
      <img src="../assets/imgs/two.jpg" alt="" class="carousel__img">
    </div>
    <div class="carousel__item carousel__item--hidden">
      <img src="../assets/imgs/three.jpg" alt="" class="carousel__img">
    </div>

    <div class="carousel__actions">
      <button class="carousel__btn carousel__btn--prev" @click.prevent="prev">Prev</button>
      <button class="carousel__btn carousel__btn--next" @click.prevent="next">Next</button>
    </div>
  </div>
</template>

<script>
  export default {

    name: "the-carousel",

    data() {
      return {
        slides: null,
        totalSlides: null,
        position: 0,

      }
    },

    created() {
      this.slides = document.getElementsByClassName('carousel__item')
      console.log(document.getElementsByClassName('carousel__item'))
      this.totalSlides = this.slides.length

    },

    methods: {

      prev() {
        console.log('previous')
        console.log('this.totalSlides', this.totalSlides)
        if (this.position === this.totalSlides - 1) {
          this.position = 0
        } else {
          this.position--
        }
        this.updateSlidePosition()
      },

      next() {
        console.log('next')
        console.log('this.totalSlides', this.totalSlides)
        if (this.position == 0) {
          this.position = 0
        } else {
          this.position++
        }
        this.updateSlidePosition()
        console.log('this.position', this.position)
      },

      updateSlidePosition() {
        for (let slide of this.slides){
          slide.classList.remove('carousel__item--visible')
          slide.classList.add('carousel__item--hidden')
          console.log('slide', slide)
        }
        this.slides[this.position].classList.add('carousel__item--visible')
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .carousel {
    height: auto;
    overflow: hidden;
    max-width: 600px;
    position: relative;

  }

  .carouse .carousel__item .carousel__item--hidden {
    display: none;
  }

  .carouse .carousel__item .carousel__item--visible {
    display: block;
  }

  .carousel__img {
    height: auto;
    width: 100%;
    max-width: 600px;
    object-fit: cover;
    object-position: center;
  }

  .carousel__item--hidden {
    display: none;
  }

  .carousel__item--visible {
    display: block;
  }

  .carousel__actions {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    width: 100%;
    display: flex;
    justify-content: space-between;
  }

  .carousel__btn {
    padding: 5px 10px;
    border: 2px solid white;
    background: transparent;
    color: white;
    font-weight: 700;
    cursor: pointer;
    outline: none;
  }

  .carousel__btn--prev {
    margin-left: 16px;
  }

  .carousel__btn--next {
    margin-right: 16px;
  }
</style>
