<script>
  import { onMount } from 'svelte';
  import { gsap } from 'gsap';
  import { ScrollTrigger } from 'gsap/ScrollTrigger';
  // Section Pinning
  onMount(() => {
    gsap.registerPlugin(ScrollTrigger);

    gsap.utils.toArray('.section').forEach((section) => {
      if (section.classList.contains('horizontal')) {
        const cardsWrap = section.querySelector(
          '.section__cards'
        );
        const oneCard = section.querySelector(
          '.section__card'
        );

        gsap.to(cardsWrap, {
          x: () => {
            return -(
              cardsWrap.scrollWidth -
              window.innerWidth +
              window.innerWidth * 0.05 +
              (window.innerWidth / 2 -
                oneCard.offsetWidth / 2)
            );
          },
          ease: 'none',
          scrollTrigger: {
            trigger: section,
            start: () => 'center center',
            end: () => '+=' + cardsWrap.scrollWidth,
            scrub: true,
            pin: true,
            invalidateOnRefresh: true,
            anticipatePin: 1,
          },
        });
      } else {
        ScrollTrigger.create({
          markers: true,
          trigger: section,
          start: () => 'top top',
          pin: true,
          anticipatePin: 1,
          // pinSpacing: true,
        });
      }
    });
  });
</script>

<a href="/">Back</a>

<section class="section --red">
  <div class="section__card">
    <h1 class="section__title">Section 1</h1>
  </div>
</section>

<section class="section">
  <div class="section__card">
    <h1 class="section__title">Section 2</h1>
  </div>
</section>

<section class="section horizontal">
  <div class="section__cards">
    <div class="section__card">
      <h1 class="section__title">Section 3a</h1>
    </div>
    <div class="section__card">
      <h1 class="section__title">Section 3b</h1>
    </div>
    <div class="section__card">
      <h1 class="section__title">Section 3c</h1>
    </div>
  </div>
</section>

<section class="section">
  <div class="section__card">
    <h1 class="section__title">Section 4</h1>
  </div>
</section>

<style>
  body {
    overflow-x: hidden;
    background-color: #1b2b34;
    width: 100vw;
  }

  .section {
    height: 100vh;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    box-sizing: border-box;
  }

  .section__cards {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    width: 100%;
    height: 100%;
    flex-shrink: 0;
  }

  .section__card {
    background-color: coral;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    flex-shrink: 0;
    justify-content: center;
    
  }

  .section__title {
    color: #1b2b34;
  }
</style>
