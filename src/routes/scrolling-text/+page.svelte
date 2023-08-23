<a href="/">Back</a>
<br />
<h1>Scrolling Text</h1>
<br />
<br />
<div class="marquee">
  <span>Mathew Bravo</span>
  <span>Mathew Bravo</span>
  <span>Mathew Bravo</span>
  <span>Mathew Bravo</span>
  <span>Mathew Bravo</span>
  <span>Mathew Bravo</span>
</div>

<style>
  .marquee {
    width: 100%;
    margin: 0 auto;
    overflow: hidden;
    white-space: nowrap;
  }

  .marquee span {
    display: inline-block;
    font-size: 20rem;
    position: relative;
    left: 100%;
    animation: marquee 36s linear infinite; /* Increased duration */
  }

  .marquee span:nth-child(1) {
    animation-delay: 0s;
  }
  .marquee span:nth-child(2) {
    animation-delay: 6s;
  } /* Increased delay */
  .marquee span:nth-child(3) {
    animation-delay: 12s;
  } /* Increased delay */
  .marquee span:nth-child(4) {
    animation-delay: 18s;
  } /* Increased delay */
  .marquee span:nth-child(5) {
    animation-delay: 24s;
  } /* Increased delay */
  .marquee span:nth-child(6) {
    animation-delay: 30s;
  } /* Increased delay */

  @keyframes marquee {
    0% {
      left: 100%;
    }
    100% {
      left: -100%;
    }
  }
</style>
