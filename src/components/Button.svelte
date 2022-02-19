<script lang="ts">
  import { candyMachineState, userState } from "../lib/store";
  import { mintOneToken } from "../lib/mint";
  import {
    getUserBalance,
    connectWallet,
    existsOwnerSPLToken,
  } from "../lib/state-helpers";
  import { web3 } from "@project-serum/anchor";
  import { awaitTransactionSignatureConfirmation } from "../lib/connection";
  import confetti from "canvas-confetti";
  import { LAMPORTS_PER_SOL } from "@solana/web3.js";
  import { onMount } from "svelte";

  const txTimeout = 30000;
  const cluster = import.meta.env.VITE_APP_SOLANA_NETWORK?.toString();
  let { solana } = window as any;
  export let connection;

  async function connectWalletButton() {
    $userState.walletPublicKey = await connectWallet(solana);
    if ($userState.walletPublicKey) {
      // Get User Balance
      $userState.userBalance = await getUserBalance(
        $userState.walletPublicKey,
        connection
      );
    }
  }

  function getPhantomWallet() {
    // Here we check for the solana object again.
    // If its present, reload the page so state is refreshed.
    solana = (window as any).solana;
    if (solana) {
      location.reload();
    } else {
      window.open("https://phantom.app/", "_blank");
    }
  }

  onMount(() => {
    solana = (window as any).solana;
  });
</script>

<div class="flex flex-col">
  {#if !solana}
    <button
      class=" px-3 py-2 rounded-md  bg-sky-600  hover:bg-sky-700 text-white font-bold" style="max-width: 200px"
      on:click={() => getPhantomWallet()}>Get Phantom Wallet</button
    >
  {:else if !$userState.walletPublicKey}

    <div class="flex">
      <span class=" my-auto text-gray-600 text-sm">
      <button
      class=" px-3 py-2 rounded-md  bg-sky-600  hover:bg-sky-700 text-white font-bold" style=""
      on:click={connectWalletButton}>Connect Wallet</button
      >
      </span>
    </div>
  {/if}
</div>
