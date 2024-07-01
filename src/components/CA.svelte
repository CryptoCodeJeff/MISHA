<script lang="ts">
  let ca = '2ePDJUwAb7SeuFovCikS9LFS9CX9tj5WMtrpANeYpump'
  let show = false

  const copy = () => {
    navigator.clipboard.writeText('2ePDJUwAb7SeuFovCikS9LFS9CX9tj5WMtrpANeYpump')
    show = true

    setTimeout(() => (show = false), 1000)
  }
</script>

<style lang="scss">
  @import 'src/sass/mixins.scss';

  button {
    position: relative;
    transition: 0.3s ease !important;
    display: block;
    font-family: 'Poppins', sans-serif;
    font-size: 30px;
    text-align: center;
    padding: 15px;
    border: 3px solid black;
    border-radius: 50px;
    width: 100%;
    margin: auto;
    background-color: var(--colorBrand);
    box-shadow: 10px 10px 30px 0px rgba(0, 0, 0, 0.3);

    @include notDesktop {
      font-size: 10px;
    }

    &:hover {
      box-shadow: 0px 0px 0px 0px rgba(0, 0, 0, 0.3);
      transform: scale(0.9);
    }
  }
</style>

<button class="link" on:click={copy}> CA: {show ? 'Copied to clipboard!' : ca} </button>
