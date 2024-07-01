<script lang="ts">
  import Svg from './Svg.svelte'

  import { confetti } from '@tsparticles/confetti'
  const images = ['a', 'b', 'c', 'real', 'd', 'e']

  let index: number = 0
  let paused: boolean = false
  let win: boolean = false

  setInterval(() => {
    if (!paused) {
      index = images.length - 1 > index ? index + 1 : 0
    }

    win = paused && index === 3
  }, 150)

  const click = () => {
    paused = !paused
  }

  const playConffeti = async () => {
    await confetti('tsparticles', {
      particleCount: 200,
      spread: 100,
    })
  }

  $: if (win) playConffeti()
</script>

<style lang="scss">
  #tsparticles {
    position: fixed;
    width: 100%;
    height: 100%;
    left: 0;
  }

  .game {
    max-width: 300px;
    img {
      object-fit: cover;
      border-radius: 10px;
    }

    .info {
      display: flex;
      justify-content: space-between;
    }
  }

  .section {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;

    .socials {
      transition: 0.5s;
      padding: 50px 0;
      opacity: 0;

      &.win {
        opacity: 1;
      }

      :global(svg) {
        width: 80px;
        height: 80px;
      }
    }
  }

  .button-name {
    width: 120px;
    align-items: center;
    appearance: none;
    background-color: #fcfcfd;
    border-radius: 4px;
    border-width: 0;
    box-shadow:
      rgba(45, 35, 66, 0.2) 0 2px 4px,
      rgba(45, 35, 66, 0.15) 0 7px 13px -3px,
      #d6d6e7 0 -3px 0 inset;
    box-sizing: border-box;
    color: #36395a;
    cursor: pointer;
    display: inline-flex;
    font-family: 'JetBrains Mono', monospace;
    height: 48px;
    justify-content: center;
    line-height: 1;
    list-style: none;
    overflow: hidden;
    padding-left: 16px;
    padding-right: 16px;
    position: relative;
    text-align: left;
    text-decoration: none;
    transition:
      box-shadow 0.15s,
      transform 0.15s;
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
    white-space: nowrap;
    will-change: box-shadow, transform;
    font-size: 18px;
  }

  .button-name:focus {
    box-shadow:
      #d6d6e7 0 0 0 1.5px inset,
      rgba(45, 35, 66, 0.4) 0 2px 4px,
      rgba(45, 35, 66, 0.3) 0 7px 13px -3px,
      #d6d6e7 0 -3px 0 inset;
  }

  .button-name:hover {
    box-shadow:
      rgba(45, 35, 66, 0.3) 0 4px 8px,
      rgba(45, 35, 66, 0.2) 0 7px 13px -3px,
      #d6d6e7 0 -3px 0 inset;
    transform: translateY(-2px);
  }

  .button-name:active {
    box-shadow: #d6d6e7 0 3px 7px inset;
    transform: translateY(2px);
  }
</style>

<div id="tsparticles"></div>

<div class="section">
  <div class="game">
    <img src="/assets/memes/{images[index]}.jpg" alt="miau" width="300px" height="300px" />

    <div class="info">
      <h3>Find the real Misha</h3>

      <button class="button-name" on:click={click}>
        {paused ? 'Resume' : 'Pause'}
      </button>
    </div>
  </div>

  <div class="socials" class:win>
    <a href="https://t.me/mishamemecoin" target="_blank">
      <Svg name="telegram" />
    </a>
    <a href="https://pump.fun/2ePDJUwAb7SeuFovCikS9LFS9CX9tj5WMtrpANeYpump" target="_blank">
      <Svg name="pump" />
    </a>
    <a href="https://x.com/FeedEveryBonk" target="_blank">
      <Svg name="twitter" />
    </a>
    <a href="" target="_blank">
      <Svg name="dexscreener" />
    </a>
  </div>
</div>
