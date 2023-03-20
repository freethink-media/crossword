<script>
  import Crossword from "../src/Crossword.svelte";
  import dataNYTDaily from "./data/nyt-daily.json";
  import dataNYTDailyMini from "./data/nyt-mini.json";
  import dataNYTDailyMiniState from "./data/nyt-mini-state.json";
  // import savedState from "./savedState.js";

  // console.log(savedState);

  function onComplete() {
    console.log('onComplete');
  }

  function onCellChange(event) {
    console.log('onCellChange', event);
  }

</script>

<article>
  <section id="default">
    <div class="info">
      <h2><a href="#default">Default Example</a></h2>
      <p>
        A
        <a href="https://www.nytimes.com/crosswords/game/daily/2020/10/21"
          >NYT daily</a
        >
        puzzle with all default settings. hello world!

      </p>
    </div>
    <Crossword data="{dataNYTDailyMini}" on:complete={onComplete} on:cellChange={onCellChange} state={dataNYTDailyMiniState} />
  </section>

  <section id="simple-customization">
    <div class="info">
      <h2><a href="#simple">With TIimer</a></h2>
      <p>
        With timer
      </p>
    </div>
    <Crossword
      data="{dataNYTDaily}"
      actions="{["clear", "reveal", "timer"]}"
    />
  </section>

  <section id="slots">
    <div class="info">
      <h2><a href="#slots">Slots</a></h2>
      <p>Custom slots for the toolbar and completion message.</p>
    </div>
    <Crossword data="{dataNYTDaily}">
      <div
        class="toolbar"
        slot="toolbar"
        let:onClear
        let:onReveal
        style="background: #333; padding: 1em; margin: 1em 0;"
      >
        <button
          style="font-size: 1.5em; background-color: #888;"
          on:click="{onClear}">clear puzzle</button
        >
        <button
          style="font-size: 1.5em; background-color: #888;"
          on:click="{onReveal}">show answers</button
        >
      </div>
      <div slot="message">
        <h3>OMG, congrats!</h3>
        <img
          alt="celebration"
          src="https://media3.giphy.com/media/QpOZPQQ2wbjOM/giphy.gif"
        />
      </div>
    </Crossword>
  </section>
</article>

<style>
  article {
    max-width: 960px;
    margin: 0 auto;
    padding: 1em;
    font-family: sans-serif;
  }
  section {
    max-width: 960px;
    margin: 5em 0;
  }

  .info {
    max-width: 640px;
    margin: 1em 0;
    text-align: left;
    font-size: 1.125em;
  }
  .info a {
    margin-right: 0.25em;
  }
  h2 {
    font-size: 1.5em;
    padding-top: 1em;
  }
  p {
    margin: 1em auto;
  }
  button {
    cursor: pointer;
  }
</style>
