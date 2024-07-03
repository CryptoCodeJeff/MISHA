<script lang="ts">
  import Svg from '@/components/Svg.svelte'
  export let company: string = '$MISHA, All rights reserved'
  export let logo: string = ''

  const socials = [
    {
      name: 'twitter',
      url: 'url',
    },
    {
      name: 'whatsapp',
      url: 'url',
    },
    {
      name: 'instagram',
      url: 'url',
    },
  ]

  const links = [
    {
      title: 'About me',
      href: '',
    },
    {
      title: 'Contact',
      href: '',
    },
    {
      title: 'FAQs',
      href: '',
    },
  ]
</script>

<style lang="scss">
  footer {
    position: relative;
    width: 100%;
    height: fit-content;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    margin-top: 200px;

    .legal-section {
      padding-top: 20px;
      display: flex;
      align-items: center;
      flex-direction: column;

      transform: scale(0.85);
      font-size: 20px;
      margin-bottom: 10px;

      color: var(--colorText2);

      p {
        text-align: center;
      }
    }
  }
</style>

<footer>
  <div class="legal-section">
    <p>
      $MISHA is a meme coin for fun, with no real value or profit expectation. By buying $MISHA, you agree you've read and understood this.
    </p>
    <div>© {new Date().getFullYear()} {company}</div>
  </div>
</footer>
