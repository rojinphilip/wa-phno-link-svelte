<script>
  import { createEventDispatcher } from 'svelte';

  let phoneNumber = '';
  let whatsappLink = '';
  let showHelpMessage = false;

  const dispatch = createEventDispatcher();

  function generateLink() {
    if (phoneNumber.trim() === '') {
      alert('Please enter a phone number.');
      return;
    }

    if (!/^\d{10}$/.test(phoneNumber.trim())) {
      alert('Please enter a 10-digit phone number.');
      return;
    }

    whatsappLink = `https://api.whatsapp.com/send?phone=${encodeURIComponent(phoneNumber)}`;
  }
</script>

<style>
  /* Styles for desktop */
  @media only screen and (min-width: 768px) {
    .container {
      max-width: 400px;
      margin: 0 auto;
    }
  }

  /* Styles for mobile */
  @media only screen and (max-width: 767px) {
    .container {
      padding: 20px;
    }

    input {
      width: 100%;
      margin-bottom: 10px;
    }

    button {
      width: 100%;
    }
  }

  .top-banner {
    background-color: #007bff;
    color: #fff;
    padding: 10px;
    text-align: center;
    margin-bottom: 10px;
    position: relative;
  }

  .help-icon {
    position: absolute;
    top: 50%;
    right: 10px;
    transform: translateY(-50%);
    cursor: pointer;
  }

  .help-message {
    position: absolute;
    top: calc(100% + 10px);
    left: 50%;
    transform: translateX(-50%);
    background-color: #007bff;
    color: #fff;
    padding: 10px;
    border-radius: 5px;
    display: none;
  }

  .help-message.show {
    display: block;
  }
</style>

<div class="top-banner">
  Chat without Saving
  <span class="help-icon" on:keypress={() => showHelpMessage = !showHelpMessage}>?</span>
  <div class="help-message" class:show={showHelpMessage}>
    <p>1. Enter the unsaved phone number and click on the 'chat' button</p>
    <p>2. Click on the Whatsapp link generated to start chatting</p>
  </div>
</div>

<div class="container">
  <input type="tel" id="phoneNumber" bind:value={phoneNumber} placeholder="Enter phone number" />

  <button on:click={generateLink}>Chat</button>

  {#if whatsappLink}
    <p>
      WhatsApp Chat Link: <a href={whatsappLink} target="_blank">{whatsappLink}</a>
    </p>
  {/if}
</div>
