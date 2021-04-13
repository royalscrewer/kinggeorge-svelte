
<script>
  import { onMount } from "svelte";
  import anime from "animejs/lib/anime.es.js";
  import { link } from "svelte-spa-router";
  import { _index } from "../stores/whatStore.js";

  let y, pageX, pageY;
  let w1 = false, w2 = false, w3 = false, w4 = false, w5 = false, w6 = false, w7 = false;

  let textWrapper;
  let subWrapper;

  function mouseHandler(e) {
    const rect = e.currentTarget.getBoundingClientRect()
    pageX = e.clientX/80;
    pageY = e.clientY/80;
  }
  

  onMount(() => {
    console.log($_index);
    textWrapper.innerHTML = textWrapper.textContent.replace(
      /([^\x00-\x80]|\w)/g,
      "<span class='letter'>$&</span>"
    );
    subWrapper.innerHTML = subWrapper.textContent.replace(
      /\S/g,
      "<span class='letter'>$&</span>"
    );

    anime
      .timeline({ loop: false })
      .add({
        targets: ".ml11 .line",
        scaleY: [0, 1],
        opacity: [0.5, 1],
        easing: "easeOutExpo",
        duration: 300,
      })
      .add({
        targets: ".ml11 .line",
        translateX: [
          0,
          document.querySelector(".ml11 .letters").getBoundingClientRect()
            .width + 10,
        ],
        easing: "easeOutExpo",
        duration: 500,
        delay: 100,
      })
      .add({
        targets: ".ml11 .letter",
        opacity: [0, 1],
        easing: "easeOutExpo",
        duration: 300,
        offset: "-=775",
        delay: (el, i) => 34 * (i + 1),
      })
      .add({
        targets: ".ml11",
        opacity: 1,
        duration: 500,
        easing: "easeOutExpo",
        delay: 100,
      })
      .add({
        targets: ".ml11 .line",
        opacity: 0,
        duration: 100,
        easing: "easeOutExpo",
        delay: 100,
      });
  });
</script>

<svelte:window bind:scrollY={y} />

<svelte:head>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.2.6/gsap.min.js" integrity="sha256-3arngJBQR3FTyeRtL3muAGFaGcL8iHsubYOqq48mBLw=" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/110/three.min.js" integrity="sha256-gSh8eotzb/CVvCREGPUNgIWuDnTYnZvVOQnRrP1eDjI=" crossorigin="anonymous"></script>
</svelte:head>

<main>
  <div class="section-1">
    <h1 style="transform: translate(0,{-y * 0.55}px)" class="ml11">
      <span class="text-wrapper">
        <span class="line line1" />
        <span bind:this={textWrapper} class="letters">King George</span>
      </span>
    </h1>
    <h2
      style="transform: translate(0,{-y * 0.85}px)"
      bind:this={subWrapper}
      class="ml16"
    >
      mad creative agency
    </h2>
  </div>
  <div class="section section-2">
    <div class="sec2-wrapper">
      <p>
        lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum
        lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum
        lorem ipsum lorem ipsum lorem ipsum lorem ipsum
      </p>
      <h3 class="idx-sub">
        King<br /> George<br /> <span class="idx-time">in 40 seconds</span>
      </h3>
      <div class="full-width" />
    </div>
  </div>
  <div class="section section-3">
    <h3 style="transform: translate({1600 - y * 1}px,0)" class="our-cases">
      Our <span class="tt-cases">cases</span> Our
      <span class="tt-cases">cases</span>
      Our <span class="tt-cases">cases</span> Our
      <span class="tt-cases">cases</span>
      Our <span class="tt-cases">cases</span>
    </h3>
    <div class="case-wrap">
      <div class="case">
        <p>Yalo</p>
        <div class="case-hover">
          <ul class="ch-tags">
            <li>Strategy /</li>
            <li>Branding & graphic</li>
            <li>Design / PR &</li>
            <li>Influencer</li>
          </ul>
          <h4>Yalo</h4>
          <h5>Yalo</h5>
        </div>
      </div>
    </div>
    <a href="/our-cases">Check our cases</a>
  </div>
  <div class="section-4" on:mousemove={mouseHandler}>
    
    <h2 style="transform: translate({pageX}px, {pageY}px)" class="what-title">
      What <br /><span class="what-title-span">we do</span>
    </h2>
    <ol class="what-nav">
      <!-- voor mobiel zonder href op de hovers-->
      <li>
        <a use:link on:mouseover={() =>{ w1 = true; w2 = false; w3 = false; w4 = false; w5 = false; w6 = false; w7 = false}} class={w1 ? "wactive" : "whata"} href="/what-we-do/strategy">Strategy</a>
      </li> 
      <li >
        <a use:link on:mouseover={() =>{ w1 = false; w2 = true; w3 = false; w4 = false; w5 = false; w6 = false; w7 = false}} class={w2 ? "wactive" : "whata"} href="/what-we-do/branding"
          >Branding & Graphic Design</a
        >
      </li>
      <li >
        <a use:link on:mouseover={() =>{ w1 = false; w2 = false; w3 = true; w4 = false; w5 = false; w6 = false; w7 = false}} class={w3 ? "wactive" : "whata"} href="/what-we-do/pr">Pr & influencer</a>
      </li>
      <li >
        <a use:link on:mouseover={() =>{ w1 = false; w2 = false; w3 = false; w4 = true; w5 = false; w6 = false; w7 = false}} class={w4 ? "wactive" : "whata"} href="/what-we-do/social">Social Media</a>
      </li>
      <li>
        <a use:link on:mouseover={() =>{ w1 = false; w2 = false; w3 = false; w4 = false; w5 = true; w6 = false; w7 = false}} class={w5 ? "wactive" : "whata"} href="/what-we-do/digital">Web-en Digital</a>
      </li>
      <li >
        <a use:link on:mouseover={() =>{ w1 = false; w2 = false; w3 = false; w4 = false; w5 = false; w6 = true; w7 = false}} class={w6 ? "wactive" : "whata"} href="/what-we-do/interior">Interior Design</a
        >
      </li>
      <li >
        <a use:link on:mouseover={() =>{ w1 = false; w2 = false; w3 = false; w4 = false; w5 = false; w6 = false; w7 = true}} class={w7 ? "wactive" : "whata"} href="/what-we-do/content">Content</a>
      </li>
    </ol>
    {#if w1}
    <h3 style="transform: translate({pageX}px, {pageY}px)" class="what-h3"><span class="what-num">01</span> Strategy</h3>
    <a style="transform: translate({pageX}px, {pageY}px)" use:link href="/what-we-do/strategy" class="what-overview">Overview</a>
 {/if}
 {#if w2}
 <h3 style="transform: translate({pageX}px, {pageY}px)" class="what-h3"><span class="what-num">02</span> Branding &<br>Graphic Design</h3>
 <a style="transform: translate({pageX}px, {pageY}px)" use:link href="/what-we-do/strategy" class="what-overview">Overview</a>
{/if}
{#if w3}
<h3 style="transform: translate({pageX}px, {pageY}px)" class="what-h3"><span class="what-num">03</span> Pr & Influencer</h3>
<a style="transform: translate({pageX}px, {pageY}px)" use:link href="/what-we-do/strategy" class="what-overview">Overview</a>
{/if}
{#if w4}
<h3 style="transform: translate({pageX}px, {pageY}px)" class="what-h3"><span class="what-num">04</span> Social Media</h3>
<a style="transform: translate({pageX}px, {pageY}px)" use:link href="/what-we-do/strategy" class="what-overview">Overview</a>
{/if}
{#if w5}
<h3 style="transform: translate({pageX}px, {pageY}px)" class="what-h3"><span class="what-num">05</span> Web-en digital</h3>
<a style="transform: translate({pageX}px, {pageY}px)" use:link href="/what-we-do/strategy" class="what-overview">Overview</a>
{/if}
{#if w6}
<h3 style="transform: translate({pageX}px, {pageY}px)" class="what-h3"><span class="what-num">06</span> Interior Desgin</h3>
<a style="transform: translate({pageX}px, {pageY}px)" use:link href="/what-we-do/strategy" class="what-overview">Overview</a>
{/if}
{#if w7}
<h3 style="transform: translate({pageX}px, {pageY}px)" class="what-h3"><span class="what-num">07</span> Content</h3>
<a style="transform: translate({pageX}px, {pageY}px)" use:link href="/what-we-do/strategy" class="what-overview">Overview</a>
{/if}
  </div>
  <div class="section-5">
    <h3 class="journal-h3">Journal</h3>
    <a use:link href="/journal" class="journal-posts">All <span class="what-title-span">posts</span></a>
    <hr>
  </div>
  <div class="section-6">
    <h2 style="transform: translate({pageX}px, {pageY}px)" class="client-title">
      Our <br /><span class="what-title-span">clients</span>
    </h2>
    <a use:link href="/clients" class="clients-all">See <span class="what-title-span">all clients</span></a>
  </div>
</main>

<style>
  main {
    text-align: center;
    margin: 0;
    padding: 0;
  }

  .full-width {
    width: 110vw;
    height: 45vw;
    background-color: black;
    position: relative;
    top: 18vh;
    left: 50%;
    right: 50%;
    margin-left: -55vw;
    margin-right: -50vw;
    z-index: 2;
  }
  .section-1 {
    position: relative;
    padding: 10rem 0;
    width: 100vw;
    background-color: var(--rose);
  }

  .section {
    margin-top: 15%;
    width: 100vw;
    height: 70vh;
    text-align: left;
  }

  .sec2-wrapper {
    box-sizing: border-box;
    position: absolute;
    left: 0;
    padding-top: 10vw;
    padding-left: 10vw;
    width: 93.5vw;
    background-color: darkblue;
    height: 105rem;
    color: white !important;
  }

  .sec2-wrapper::after {
    position: absolute;
    bottom: 5%;
    left: 0;
    content: "";
    width: 95vw;
    background-color: yellow;
    height: 90rem;
    z-index: -1;
  }

  .sec2-wrapper p,
  .sec2-wrapper h3 {
    z-index: 10;
    position: absolute;
  }

  .sec2-wrapper p {
    margin-bottom: 5rem;
    position: relative;
    color: white;
    padding-right: 10vw;
  }

  .section-3 {
    padding-top: 50rem;
    position: relative;
    height: 505vh;
  }

  .section-4 {
    margin-top: 50rem;
    width: 73vw;
    height: 75vh;
    margin: 0 2vw 0 4vw;
    padding: 5rem 10vw;
    text-align: left;
    position: relative;
    background-color: var(--rose);
  }

  .what-nav {
    text-transform: uppercase;
    font-family: "Galano", sans-serif;
    font-size: 1.4rem;
    font-weight: 600;
    letter-spacing: 1px;
    list-style: decimal-leading-zero;
  }

  .what-nav a {
    opacity: 1;
    color: white;
    list-style-position: outside;
  }

  .what-nav li {
    padding-left: 35px;
    line-height: 3rem;
    cursor: pointer;
    transform: translateX(-65px);
  }

  .wactive {
    color: #141456 !important;
    font-size: 2rem;
  }


  .what-nav li::marker {
    color: white;
    font-weight: 300;
    font-size: 1.2rem;
  }

  .what-title {
    font-size: 6rem;
    text-transform: capitalize;
    font-family: "Galano", sans-serif;
    color: white;
  }

  .what-title-span {
    text-transform: lowercase;
    font-weight: 400;
    font-family: "Canela", Tahoma, Geneva, Verdana, sans-serif;
  }

  .what-h3 {
    position: absolute;
    right: 0;
    bottom: 0;
    transform: translateX(2rem);
    color: white;
    font-size: 7rem;
    text-shadow: 2px 4px 4px rgba(0,0,0,0.2),
                 0px -5px 10px rgba(255,155,155,0.15);
    animation: 100ms h3appear ease-out;
    font-family: "Galano", sans-serif;
    text-transform: uppercase;
  }

  .what-overview {
    color: white;
    font-size: 2.4rem;
    font-weight: bold;
    position: absolute;
    right: 10vw;
    bottom: 5vh;
    font-family: "Galano", sans-serif;
    text-shadow: 2px 4px 4px rgba(0,0,0,0.2),
                 0px -5px 10px rgba(255,155,155,0.15);
    animation: 300ms h3appear ease-out;

  }

  .what-overview::after {
    content: "↘";
    font-weight: 300;
    margin-left: 25px;
  }

  .what-overview {background-image: linear-gradient(to right, #DD5E8900 0%, #F7BB9700  50%, #97dcf7  50.1%,  var(--blue)  100%)}

.what-overview {
   margin: 10px;
   text-align: center;
   text-transform: uppercase;
   transition: 100ms;
   background-size: 200% auto;
   color: white;            
   display: block;
 }

 .what-overview:hover {
   background-position: right center; /* change the direction of the change here */
   color: #fff;
   text-decoration: none;
 }

  .section-5 {
    margin: 0 2vw 0 4vw;
    padding: 5rem 10vw;
    text-align: left;
    position: relative;

  }

  .journal-h3 {
    color: var(--blue);
    font-size: 7rem;
    font-family: "Galano", sans-serif;
    text-transform: capitalize;
    margin-bottom: 1rem;
  }


  .journal-posts {background-image: linear-gradient(to right, #DD5E8900 0%, #F7BB9700  50%, #97dcf7  50.1%,  var(--blue)  100%)}

         .journal-posts {
            margin: 10px;
            text-align: center;
            text-transform: capitalize;
            transition: 100ms;
            background-size: 200% auto;
            color: white;            
            display: block;
          }

          .journal-posts:hover {
            background-position: right center; /* change the direction of the change here */
            color: #fff;
            text-decoration: none;
          }
         
  .journal-posts {
    color: var(--blue);
    font-size: 2.4rem;
    font-weight: bold;
    position: absolute;
    right: 10vw;
    bottom: 8rem;
    font-family: "Galano", sans-serif;

  }

  .journal-posts::after {
    content: "↘";
    font-weight: 300;
    margin-left: 25px;
  }

  .section-6 {
    margin: 0 2vw 0 4vw;
    padding: 5rem 10vw;
    text-align: left;
    position: relative;
  }

  .client-title {
    color: var(--blue);
    font-size: 7rem;
    font-family: "Galano", sans-serif;
    text-transform: lowercase;
    margin-bottom: 1rem;
  }

  .clients-all {background-image: linear-gradient(to right, #DD5E8900 0%, #F7BB9700  50%, #97dcf7  50.1%,  var(--blue)  100%)}

.clients-all {
   margin: 10px;
   text-align: center;
   text-transform: capitalize;
   transition: 100ms;
   background-size: 200% auto;
   color: white;            
   display: block;
 }

 .clients-all:hover {
   background-position: right center; /* change the direction of the change here */
   color: #fff;
   text-decoration: none;
 }

.clients-all {
color: var(--blue);
font-size: 2.4rem;
font-weight: bold;
position: absolute;
right: 10vw;
bottom: 8rem;
font-family: "Galano", sans-serif;

}

.clients-all::after {
content: "↘";
font-weight: 300;
margin-left: 25px;
}


  @keyframes h3appear {
    0% {
      filter: blur(5px);
      transform: translateX(10rem);
    }
  }

  .what-num {
    font-size: 3.5rem;
  }

  h1 {
    color: white;
    text-transform: uppercase;
    font-family: "Galano", sans-serif;
  }

  h2 {
    font-size: 3rem;
    font-family: "Canela", Tahoma, Geneva, Verdana, sans-serif;
  }

  .ml16 {
    position: absolute;
    top: 15rem;
    left: 45%;
    color: white;
    font-weight: 800;
    font-size: 3rem;
    text-align: left;
    text-transform: uppercase;
    width: 10rem;
    animation: appearsub 5s cubic-bezier(0.19, 1, 0.42, 1) forwards;
  }

  @keyframes appearsub {
    0% {
      opacity: 0;
    }

    50% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  .ml11 {
    position: relative;
    left: 8vw;
    text-align: left;
    font-weight: 700;
    font-size: 12rem;
    line-height: 12rem;
    max-width: 14rem;
  }

  .ml11 .text-wrapper {
    position: relative;
  }

  .ml11 .line {
    opacity: 0;
    position: absolute;
    left: 0;
    height: 100%;
    width: 3px;
    background-color: #fff;
    transform-origin: 0 50%;
  }

  .ml11 .line1 {
    top: 0;
    left: 0;
  }

  .ml11 .letters {
    line-height: 1em;
  }

  p {
    font-size: 2.2rem;
    max-width: 14rem;
    margin: 2rem auto;
    line-height: 1.35;
  }

  .idx-sub {
    text-align: left;
    font-family: "Galano", sans-serif;
    font-size: 7rem;
  }

  .idx-time {
    font-family: "Canela", sans-serif;
  }

  .our-cases {
    font-size: 10rem;
    text-transform: lowercase;
    font-family: "Galano", sans-serif;
    width: 300vw;
    color: var(--blue);
    position: relative;
    z-index: 200;
  }

  .tt-cases {
    font-family: "Canela", Tahoma, Geneva, Verdana, sans-serif;
    font-weight: 500;
  }

  .case-wrap {
    background-color: var(--grey);
    position: absolute;
    left: 0;
    width: 100vw;
    height: 500vh;
    transform: translateY(-16rem);
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }

  /* deze waarschijnlijk naar een component */

  .case-hover {
    opacity: 0;
  }

  .case {
    position: relative;
    top: 20rem;
    width: 45vw;
    height: 40rem;
    background: black;
  }

  .case:hover .case-hover {
    display: grid;
    place-items: center;
    position: relative;
    grid-template-rows: 4rem 1fr 4rem;
    top: -40%;
    left: 5%;
    opacity: 1;
    width: 100%;
    height: 100%;
    background-color: rgba(255, 0, 0, 0.356);
    font-weight: 700;
    font-family: "Galano", sans-serif;
    transition: 250ms cubic-bezier(0.215, 0.61, 0.355, 1);
    cursor: pointer;
  }

  .ch-tags {
    padding-top: 5rem;
    padding-left: 5vw;
    color: white;
    font-size: 1.8rem;
    text-transform: uppercase;
    list-style: none;
    font-weight: 400;
    font-family: "Galano", sans-serif;
    position: relative;
    top: 5rem;
    justify-self: left;
    transition: 400ms cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  .case-hover h4 {
    font-size: 6rem;
    color: white;
  }

  .case-hover h5 {
    font-size: 6rem;
    color: white;
    position: relative;
    left: 14vw;
    top: 2rem;
    mix-blend-mode: lighten;
    animation: h5 800ms ease;
    opacity: 1;
  }

  @keyframes h5 {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  .case p {
    font-size: 14rem;
    top: -11rem;
    left: 4rem;
    font-weight: 700;
    font-family: "Galano", sans-serif;
    position: relative;
    z-index: -1;
    color: #141456;
  }
</style>
