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
  @import 'src/sass/mixins.scss';
  #tsparticles {
    position: fixed;
    width: 100%;
    height: 100%;
    left: 0;
  }

  .game {
    max-width: 320px;

    h3 {
      font-size: 25px;
      text-align: center;
    }

    img {
      object-fit: cover;
      width: 100%;
      border-radius: 10px;
    }

    .info {
      display: flex;
      justify-content: space-between;
    }
  }

  .ca {
    &.win {
      opacity: 1;
    }

    @include desktop {
      font-size: 30px;
    }
    opacity: 0;
  }

  .section {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;

    .socials {
      display: flex;
      gap: 30px;
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
    width: 100%;
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

<div id="tsparticles" style="z-index: -1;"></div>

<div class="section">
  <div class="game">
    <h3>Pause the MISHA without hat</h3>
    <img src="/assets/memes/{images[index]}.jpg" alt="miau" width="300px" height="300px" />

    <button class="button-name" on:click={click}>
      {paused ? 'Resume' : 'Pause'}
    </button>
  </div>

  <div class="socials" class:win>
    <a href="https://t.me/mishamemecoin" target="_blank">
      <Svg name="telegram" />
    </a>
    <a href="https://x.com/MishaOnSolana" target="_blank">
      <Svg name="twitter" />
    </a>
    <a href="https://pump.fun/89kNPfsS8KPxjneKywgXri3sgGYYG7QZZaLiXxcTpump" target="_blank">
      <Svg name="pump" />
    </a>
  </div>

  <p class="ca" class:win>89kNPfsS8KPxjneKywgXri3sgGYYG7QZZaLiXxcTpump</p>
</div>
