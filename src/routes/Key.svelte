<script lang="ts">
  import { onMount } from 'svelte';
  import { noteArr, pos } from './variables.ts';

  export let note;
  let classname = note.length > 2 ? "key black" : "key";
  let isActive = false;
  let audio;

  onMount(() => {
    audio = new Audio(`/sounds/${note}.mp3`);
  });



  function playSound() {
   audio = new Audio(`/sounds/${note}.mp3`);
    noteArr[pos[0]] = note;
    pos[0]++;
    console.log(noteArr);
    audio.currentTime = 0;
    audio.play();
    isActive = true;
    setTimeout(() => {
      isActive = false;
    }, 200);
  }
</script>

<style>
  .key {
    background-color: white;
    height: 300px;
    width: 60px;
    border: 2px solid black;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    cursor: pointer; 
  }

  .key:hover {
    background-color: lightgrey;
  }

  .black {
    background-color: black;
    margin-left: -17px;
    margin-right: -17px;
    height: 200px;
    width: 30px;
    z-index: 2;
  }

  .black:hover {
    background-color: darkgrey;
  }

  .active {
    background-color: grey; 
  }

  .txt {
    color: black;
    font-weight: 600;
    font-size: 36px;
    margin-bottom: 10px;
  }

  .REPLAY{
    align-items: center;
  }
</style>

<div class="{classname} {isActive ? 'active' : ''}" on:click={playSound}>
  {#if note.length === 2}
    <div class="txt">
      {note.toUpperCase()}
    </div>
  {/if}
</div>
