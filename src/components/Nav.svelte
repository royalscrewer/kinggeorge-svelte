<script>
    import { createToggle } from '../stores/navStore.js';
    import {link} from "svelte-spa-router"
  
    const display_menu = createToggle(false);
    var overlay = false;
  
  </script>

  
  <nav>
    <a class="home" href="/" use:link>  <div class="__crown-frame">
      <img class='__crown-spritesheet' src="./assets/crown-spritesheet-24.jpg" alt="Worthy of the crown"/>
    </div></a>
  
    
    {#if !$display_menu}
      <div on:click={display_menu.toggle} class="mlines">
        <div class="mline"/>
        <div class="mline"/>
      </div>
    {/if}
  </nav>
  
  {#if $display_menu}
    <div bind:this={overlay}  class="secondary-nav animate__animated {overlay ? 'animate__slideInLeft': 'animate__zoomOutLeft'}">
      <div class="close" on:click={() => {
        overlay = false;
        setTimeout(display_menu.toggle, 600);
       
        }}>
        <svg
          height="30pt"
          viewBox="0 0 311 311.07733"
          width="30pt"
          xmlns="http://www.w3.org/2000/svg"
          id="fi_1828747"
          ><path
            d="m16.035156 311.078125c-4.097656 0-8.195312-1.558594-11.308594-4.695313-6.25-6.25-6.25-16.382812 0-22.632812l279.0625-279.0625c6.25-6.25 16.382813-6.25 22.632813 0s6.25 16.382812 0 22.636719l-279.058594 279.058593c-3.136719 3.117188-7.234375 4.695313-11.328125 4.695313zm0 0"
          /><path
            d="m295.117188 311.078125c-4.097657 0-8.191407-1.558594-11.308594-4.695313l-279.082032-279.058593c-6.25-6.253907-6.25-16.386719 0-22.636719s16.382813-6.25 22.636719 0l279.058594 279.0625c6.25 6.25 6.25 16.382812 0 22.632812-3.136719 3.117188-7.230469 4.695313-11.304687 4.695313zm0 0"
          /></svg
        >
      </div>
      <ul class="snav-list">
        <a use:link href="/">Home</a>
        <a use:link href="/about">About us</a>
        <a use:link href="/our-cases">Our cases</a>
        <a use:link href="/what-we-do">What we do</a>
        <a use:link href="/blog">Blog</a>
        <a use:link href="/contact">Contact</a>
      </ul>
      <ul class="snav-footer">
        <a>Instagram</a>
        <a>Facebook</a>
        <a>Linkedin</a>
        <a>Spotify</a>
        <a><em>EN</em></a>
      </ul>
    </div>
  {/if}
  
  <style>
  
    .mlines:hover .mline {
      border-bottom: 3px solid white;
      transition: 100ms ease;
    }
  
  
    .mlines {
      display: flex;
      flex-direction: column;
      width: 40px;
      height: 30px;
      margin-right: 4vw;
      margin-top: 4vw;
      cursor: pointer;
    }
    .mline {
      border-bottom: 3px solid var(--blue);
      margin-bottom: 25%;
    }
    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 5rem;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      z-index: 999;
    }
  
    .home {
      color: var(--blue);
      margin-left: 1rem;
    }
  
    nav a + a {
      margin-right: 2rem;
      justify-self: flex-end;
    }
  
    .close {
      justify-self: flex-end;
      align-self: flex-start;
      position: absolute;
      top: 5vw;
      right: 5vw;
      cursor: pointer;
      fill: var(--blue);
    }
  
    .close:hover {
      fill: var(--rose);
    }
  
    .secondary-nav {
      box-sizing: border-box;
      width: 95vw;
      height: 90vh;
      display: grid;
      place-items: center;
      margin: auto;
      background-color: rgba(240, 248, 255, 0.4);
      box-shadow: 0 2.8px 2.2px rgba(0, 0, 0, 0.02),
        0 6.7px 5.3px rgba(0, 0, 0, 0.028), 0 12.5px 10px rgba(0, 0, 0, 0.035),
        0 22.3px 17.9px rgba(0, 0, 0, 0.042), 0 41.8px 33.4px rgba(0, 0, 0, 0.05),
        0 100px 80px rgba(0, 0, 0, 0.07);
      backdrop-filter: blur(7px);
      -webkit-backdrop-filter: blur(7px);
      border-radius: 50px;
      border: 1pt solid rgba(0, 0, 139, 0.13);
      position: fixed;
      z-index: 9999;
      top: 5vh;
      left: 2.5vw;
      padding: 5rem 5vw;
      transition: 200ms ease-in-out;
    }
  
    .snav-list {
      justify-self: flex-start;
      opacity: 1;
      cursor: pointer;
      display: flex;
      flex-direction: column;
      text-align: left;
      font-size: 3.8rem;
      font-weight: bold;
      text-transform: uppercase;
      color: #363360;
      
    }
  
    .snav-list a:hover {
      color: var(--rose);
      transform: rotateX(20deg) rotateY(5deg); 
      text-shadow: 0 2.8px 2.2px rgba(254, 97, 110, 0.02),
        0 6.7px 5.3px rgba(254, 97, 110, 0.028), 0 12.5px 10px rgba(254, 97, 110, 0.035),
        0 22.3px 17.9px rgba(254, 97, 110, 0.042), 0 41.8px 33.4px rgba(254, 97, 110, 0.05),
        0 100px 80px rgba(254, 97, 110, 0.07);
    }
  
    .snav-footer {
      display: flex;
      justify-content: space-between;
      width: 96%;
      font-size: 1.1rem;
      color: #363360;
    }
  
    .__crown-frame {
      margin-top: 6rem;
      overflow: hidden;
      height: 150px;
      width: 150px;
      border-radius: 500px;
      -moz-box-shadow: 1px 2px 3px rgba(254, 97, 110,.5);
  -webkit-box-shadow: 1px 2px 3px rgba(254, 97, 110,.5);
  box-shadow: 1px 2px 3px rgba(254, 97, 110,.5);
    }
  
    .__crown-spritesheet {
      opacity: 0.75;
      animation: turnCrown 1s steps(24) infinite;
    }
  
    .__crown-spritesheet:hover {
      opacity: 0.85;
      animation: turnCrown 1s steps(17) infinite;
    }
  
    @keyframes turnCrown {
      from {
        transform: translate3d(0px,0,0);
      }
      to {
        transform: translate3d(-100%,0,0);
      }
    }
  </style>
  