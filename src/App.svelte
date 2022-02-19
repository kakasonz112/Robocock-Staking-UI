<script lang="ts">
  import { onMount } from "svelte";
  import { Connection } from "@solana/web3.js";
  import { Provider, web3 } from "@project-serum/anchor";
  import { fade } from "svelte/transition";
  import Button from "./components/Button.svelte";
  import Header from "./components/CardHeader.svelte";
  import { LAMPORTS_PER_SOL } from "@solana/web3.js";
  import Tabs from "./components/Tabs.svelte";

  import { candyMachineState, userState } from "./lib/store";
  import {
    getCandyMachineState,
    checkWalletConnected,
    getUserBalance,
    existsOwnerSPLToken,
  } from "./lib/state-helpers";



  // List of tab items with labels and values.
  let tabItems = [
    { label: "Your COCKS", value: 1 },
    { label: "Staked COCKS", value: 2 },
    { label: "Your Rewards", value: 3 }
  ];

// Current active tab
let currentTab;

  /***********************************/
  // Customise the app by changing the following variables.
  const TITLE = "STAKE YOUR COCKS";
  const DESCRTIPTION = " ";
  const HEADER_TITLE = "Robocock.io";
  const HEADER_LINK = "https://www.robocock.io";
  // Your image or GIF needs to be in the /public folder for this to work
  const IMAGE_LINK = "";
  /***********************************/

  let { solana } = window as any;
  const rpcUrl = import.meta.env.VITE_APP_SOLANA_RPC_HOST?.toString();
  const cluster = import.meta.env.VITE_APP_SOLANA_NETWORK?.toString();
  const candyMachineId = import.meta.env.VITE_APP_CANDY_MACHINE_ID?.toString();
  const opts = { preflightCommitment: "processed" };

  let siteLoading = true;
  let errorOcurred = false;
  let connection: Connection;
  let provider: Provider;
  let candyMachinePublicKey: web3.PublicKey;

  $: itemsRedeemed = $candyMachineState?.state.itemsRedeemed;
  $: itemsAvailable = $candyMachineState?.state.itemsAvailable;
  $: date = new Date($candyMachineState?.state.goLiveDate?.toNumber() * 1000);
  $: price = $candyMachineState?.state.price;

  function checkEnvironmentVariables() {
    // Check if populated
    if (!rpcUrl || !candyMachineId || !cluster) {
      if (!rpcUrl) {
        console.error("RPC URL not populated");
      }
      if (!candyMachineId) {
        console.error("Candy Machine ID not populated");
      }
      if (!cluster) {
        console.error("Environment not populated");
      }
      return true;
    }
    if (candyMachineId.length < 32 || candyMachineId.length > 44) {
      console.error(
        "Candy Machine Public Key is invalid. Enter a length in-between 32 and 44 characters"
      );
      return true;
    }
    return false;
  }

  onMount(async () => {
    solana = (window as any).solana;
    // Check if environement variables are populated
    // errorOcurred = checkEnvironmentVariables();
    // if (errorOcurred) {
    //  return;
    // }

    // If env variables populated, create provider, PK and connection
    connection = new Connection(rpcUrl);
    provider = new Provider(
      connection,
      solana,
      opts.preflightCommitment as web3.ConfirmOptions
    );
    candyMachinePublicKey = new web3.PublicKey(candyMachineId);

    // Get candy machine state
    $candyMachineState = await getCandyMachineState(
      candyMachinePublicKey,
      provider
    );
    // Establish connection to wallet
    if (solana?.isPhantom) {
      $userState.walletPublicKey = await checkWalletConnected(solana);
      if ($userState.walletPublicKey) {
        // Get User Balance
        $userState.userBalance = await getUserBalance(
          $userState.walletPublicKey,
          connection
        );
        // If whitelist config populated, check if user is whitelisted (ie. check if they have token)

      }
    }

    // Stop loading
    siteLoading = false;
  });
</script>

<main class="h-screen">
  <!-- Error section -->
  {#if errorOcurred}
    <div class=" h-full flex">
      <div class="m-auto">
        An error occurred. Please check if your environment variables have been
        populated correctly and redeploy the applcation.
      </div>
    </div>
    <!-- Loading Section -->
  {:else if siteLoading && !errorOcurred}
    <div class=" h-full flex" style="    display: flex;
    align-items: center;
    justify-content: center;">
      <div class="loader">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  {:else}
  <Button {connection} />
    <!-- Menu Bar -->
    {#if HEADER_TITLE}
    <div class="nav">
      <a
        href={HEADER_LINK}
        class="text-white tracking-widest decoration-2 font-mono nav-link"
        style="font-family: 'Paladins Straight', sans-serif;"
        >{HEADER_TITLE}</a
      >
    </div>
    {/if}

    <!-- Card -->
    <div
      class="mx-auto bg-whitesmoke rounded-lg my-12  border-2"
      transition:fade   style="background-color: black; max-width: 50rem"
    >
      <!-- Top Bar -->
      <Header />
      <hr />
      <br />
      <!-- Main Body -->
      <div class="p-6">

    
        <div
          class=" text-lg sm:text-2xl font-mono font-bold py-5 tracking-wider"
        >
          {TITLE}
        </div>
        <div class="text-sm sm:text-md font-semibold pb-5 text-gray-600 ">
          {DESCRTIPTION}
        </div>
        
      <!-- NFT STAKING CONTENT -->
      <Tabs bind:activeTabValue={currentTab} items={tabItems} />

      <code class="language-text"></code>

      {#if 1 === currentTab}
      <h3>Tab 1 content</h3>
      <p> test</p>
      {/if}
      
      {#if 2 === currentTab}
        <h3>Tab 2 content</h3>
      {/if}
      
      {#if 3 === currentTab}
        <h3>Tab 3 content</h3>
      {/if} 

      </div>
    </div>
  {/if}
</main>
