<script>
  import Key from './Key.svelte';
  import { noteArr } from './variables.ts';
  let audio
  let isActive = false
  async function playback(){
    for(let i in noteArr){
    let youarepdf = noteArr[i];
    audio = new Audio(`/sounds/${youarepdf}.mp3`);
    audio.currentTime = 0;
    audio.play();
    await new Promise(resolve => setTimeout(resolve, 500));
    isActive = true;
    setTimeout(() => {
      isActive = true;
    }, 200);
    
    }
  }
</script>

<style>
  .piano {
    display: flex;
    flex-direction: row;
    position: fixed;
    bottom: 0;
    right: 25%;
    background-color: black;
  }

  .body {
    background-color: black;
    justify-content: flex-end;
    align-items: center;
  }

</style>

<body class="body"></body>
<button on:click={()=>playback()}>
  Playback
</button>
  <div class="piano">
    <Key note="C3" />
    <Key note="Db3" />
    <Key note="D3" />
    <Key note="Eb3" />
    <Key note="E3" />
    <Key note="F3" />
    <Key note="Gb3" />
    <Key note="G3" />
    <Key note="Ab3" />
    <Key note="A3" />
    <Key note="Bb3" />
    <Key note="B3" />
    <Key note="C4" />
    <Key note="Db4" />
    <Key note="D4" />
    <Key note="Eb4" />
    <Key note="E4" />
    <Key note="F4" />
    <Key note="Gb4" />
    <Key note="G4" />
    <Key note="Ab4" />
    <Key note="A4" />
    <Key note="Bb4" />
    <Key note="B4" />
    <Key note="C5" />
  </div>
