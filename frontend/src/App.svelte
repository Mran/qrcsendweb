<script lang="ts">
  import logo from "./assets/images/logo-universal.png";
  import { Greet } from "../wailsjs/go/main/App.js";
  import jrQrcode  from "jr-qrcode";
import { onMount } from "svelte";
  let resultText: string = "Please enter your name below 👇";
  let name: string;

  function greet(): void {
    Greet(name).then((result) => (resultText = result));
  }
  let qrcode1: any;
  onMount(() => {
    console.log("onMount");
    qrcode1=jrQrcode.getQrBase64("123")
  console.log(qrcode1);

  });
</script>

<main>
  <div class="result bg-red-100" id="result">{resultText}</div>
  <div class="bg-red-500">okok12312</div>
  <div id="test" >
    <img src={qrcode1} alt="" width="100" height="100">
  </div>
  <div class="input-box" id="input">
    <input
      autocomplete="off"
      bind:value={name}
      class="input"
      id="name"
      type="text"
    />
    <button class="btn" on:click={greet}>Greet</button>
  </div>
</main>

<style>
  #logo {
    display: block;
    width: 50%;
    height: 50%;
    margin: auto;
    padding: 10% 0 0;
    background-position: center;
    background-repeat: no-repeat;
    background-size: 100% 100%;
    background-origin: content-box;
  }

  .result {
    height: 20px;
    line-height: 20px;
    margin: 1.5rem auto;
  }

  .input-box .btn {
    width: 60px;
    height: 30px;
    line-height: 30px;
    border-radius: 3px;
    border: none;
    margin: 0 0 0 20px;
    padding: 0 8px;
    cursor: pointer;
  }

  .input-box .btn:hover {
    background-image: linear-gradient(to top, #cfd9df 0%, #e2ebf0 100%);
    color: #333333;
  }

  .input-box .input {
    border: none;
    border-radius: 3px;
    outline: none;
    height: 30px;
    line-height: 30px;
    padding: 0 10px;
    background-color: rgba(240, 240, 240, 1);
    -webkit-font-smoothing: antialiased;
  }

  .input-box .input:hover {
    border: none;
    background-color: rgba(255, 255, 255, 1);
  }

  .input-box .input:focus {
    border: none;
    background-color: rgba(255, 255, 255, 1);
  }
</style>
