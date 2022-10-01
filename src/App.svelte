<script lang="ts">
  const params = new URLSearchParams(window.location.search);
  const story = !!params.get('story');

  const candidates = [
      {
          name: 'Espaguete',
          number: '2117',
          party: 'PCB',
          position: 'Dep. Federal'
      },
      {
          name: 'Bruno Marota',
          number: '21212',
          party: 'PCB',
          position: 'Dep. Estadual'
      },
      {
          name: 'Sara Azevedo',
          number: '500',
          party: 'PSOL',
          position: 'Senadora'
      },
      {
          name: 'Kalil',
          number: '55',
          party: 'PSD',
          position: 'Governador'
      },
      {
          name: 'Lula',
          number: '13',
          party: 'PT',
          position: 'Presidente'
      },
  ]
</script>

<main class:story>
  <h1 class="title">Colinha eleições 2022</h1>
  <ul class="candidates">
    {#each candidates as candidate}
      <li>
        <figure style="background-image:url('/img/{candidate.number}.webp')" />
        <div class="details">
          <h1 class="name">
            {candidate.name}
            <span>({candidate.party})</span>
          </h1>
          <p class="position">{candidate.position}</p>
          <p class="number">
            {#each candidate.number as digit}
              <span>{digit}</span>
            {/each}
          </p>
        </div>
      </li>
    {/each}
  </ul>
</main>

<style lang="sass">
  $highlight: #6930c3

  main
    position: relative
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center
    gap: 4rem
    width: 1280px
    height: 720px
    padding: 2rem
    background-color: #070212
    color: #fff
    z-index: 1

  .title
    font-size: 3rem
    text-align: center
    font-weight: bold
    text-transform: uppercase

  .candidates
    position: relative
    display: flex
    align-items: center
    gap: 2rem

    &::before
      position: absolute
      content: ''
      width: 100%
      height: 100%
      background-color: $highlight
      border-radius: 100%
      filter: blur(4rem)
      opacity: .2
      z-index: -1

    li
      display: flex
      flex-direction: column
      align-items: center

      .details
        display: flex
        flex-direction: column
        justify-content: center
        text-align: center

      figure
        width: 215px
        aspect-ratio: 3/4
        border-radius: 1rem
        margin-bottom: 1rem
        background-color: rgba(#fff, .1)
        background-position: center
        background-repeat: no-repeat
        background-size: cover

      .name
        display: flex
        align-items: center
        gap: .25rem
        font-size: 1.5rem
        font-weight: bold

        span
          font-size: 75%
          font-weight: 400
          opacity: .75

      .position
        margin-bottom: .5rem
        opacity: .75

      .number
        display: flex
        justify-content: center
        gap: .25rem
        font-size: 1.25rem

        span
          display: flex
          justify-content: center
          align-items: center
          height: 3rem
          width: 2rem
          border-radius: .5rem
          background-color: rgba(#fff, .1)

      &:last-child
        figure
          width: 230px

        .name
          gap: .5rem
          font-size: 2.75rem
          font-weight: 800
          text-transform: uppercase

        .number span
          font-weight: bold
          background-color: $highlight

  .story
    width: 1080px
    height: 1920px
    padding: 4rem

    .title
      font-size: 4rem
      opacity: 0

    .candidates
      width: 100%
      flex-direction: column
      align-items: flex-start

      &::before
        opacity: .05

      li
        width: 100%
        flex-direction: row
        align-items: flex-start
        gap: 2rem

        .details
          justify-content: flex-start
          text-align: left

        .name
          font-size: 4rem
          gap: 1rem

          span
            font-size: 60%

        .position
          font-size: 2.5rem
          margin-bottom: 2rem

        .number
          font-size: 2.75rem
          justify-content: flex-start

          span
            width: 3.5rem
            height: 4.5rem
</style>