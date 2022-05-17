<script lang="ts">
  import { onMount } from "svelte";
  import { Connection } from "@solana/web3.js";
  import { Provider, web3 } from "@project-serum/anchor";
  import { fade } from "svelte/transition";
  import Header from "./components/CardHeader.svelte";
  import { LAMPORTS_PER_SOL } from "@solana/web3.js";
  import Tabs from "./components/Tabs.svelte";
  import Tabs_g1 from "./components/Tabs-Gen1.svelte";
  import Tabs_g2 from "./components/Tabs-Gen2.svelte";

  // List of tab items with labels and values.
  let tabItems = [
    { label: "Gen 1", value: 1 },
    { label: "Gen 2", value: 2 }
  ];

  let tabItems_g = [
    { label: "UnStaked", value: 1 },
    { label: "Staked", value: 2 }
];

// Current active tab
let currentTab;
let currentTab_g;

  /***********************************/
  // Customise the app by changing the following variables.
  const TITLE = "STAKE YOUR COCKS";
  const DESCRTIPTION = " ";
  const HEADER_TITLE = "Robocock.io";
  const HEADER_LINK = "https://www.robocock.io";
  // Your image or GIF needs to be in the /public folder for this to work
  const IMAGE_LINK = "";
  /***********************************/


  onMount(async () => {
  });
</script>

<main class="h-screen">
  <div class="background"></div>

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
      class="mx-auto bg-whitesmoke rounded-lg my-12"
      transition:fade   style="max-width: 75rem; position:relative"
    >
      <!-- Top Bar -->
      <Header />
      <hr />
      <br />
      <!-- Main Body -->
      <div class="p-6">
        <!-- Loading Animation with overlay
        <div class="loading"> 
          <div class="lds-roller"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
        </div>
        -->    
        <div class="text-center" data-v-9aebbff6="">
          <p class="mb-3" data-v-9aebbff6=""> 
            Connect your wallet to get started staking your cocks : 
          </p>
          <div class="select-box">
            <div class="select-box__current" tabindex="1">
                <div class="select-box__value"><input class="select-box__input" type="radio" id="0" value="1" name="ROBOCOCK" checked="checked" />
                    <p class="select-box__input-text">Choose Wallet</p>
                </div>
                <div class="select-box__value"><input class="select-box__input" type="radio" id="1" value="Phantom" name="ROBOCOCK" />
                    <p class="select-box__input-text">Phantom</p>
                </div>
                <div class="select-box__value"><input class="select-box__input" type="radio" id="2" value="Sollet" name="ROBOCOCK" />
                    <p class="select-box__input-text">Sollet</p>
                </div>
                <div class="select-box__value"><input class="select-box__input" type="radio" id="3" value="Sollet Extension" name="ROBOCOCK" />
                    <p class="select-box__input-text">Sollet Extension</p>
                </div>
                <div class="select-box__value"><input class="select-box__input" type="radio" id="4" value="Solflare" name="ROBOCOCK" />
                    <p class="select-box__input-text">Solflare</p>
                </div>
                <div class="select-box__value"><input class="select-box__input" type="radio" id="4" value="Solflare Web" name="ROBOCOCK" />
                  <p class="select-box__input-text">Solflare Web</p>
              </div>
                
                <img class="select-box__icon" src="http://cdn.onlinewebfonts.com/svg/img_295694.svg" alt="Arrow Icon" aria-hidden="true" />
            </div>
            <ul class="select-box__list">
                <li><label class="select-box__option" for="1" aria-hidden="aria-hidden">Phantom</label></li>
                <li><label class="select-box__option" for="2" aria-hidden="aria-hidden">Sollet</label></li>
                <li><label class="select-box__option" for="3" aria-hidden="aria-hidden">Sollet Extension</label></li>
                <li><label class="select-box__option" for="4" aria-hidden="aria-hidden">Solflare</label></li>
                <li><label class="select-box__option" for="4" aria-hidden="aria-hidden">Solflare Web</label></li>
            </ul>
          </div>
          <br><br>
        <!-- NFT STAKING CONTENT -->
        <Tabs bind:activeTabValue={currentTab} items={tabItems} />

        <code class="language-text"></code>
        <!-- Gen1 Content -->    
        {#if 1 === currentTab}
        <div class="flex justify-around mb-10" data-v-9aebbff6="">
          <div class="box">
              <div class="flex-col">
                <p>Gen1 Cocks Staked</p>
                <h1>3016</h1>
              </div>
          </div>
          <div class="box">
              <div class="flex-col">
                <p>% Gen1 Cocks Staked</p>
                <h1>78.58%</h1>
              </div>
          </div>

        </div>

        <div class="flex justify-around mb-10" data-v-9aebbff6="">
          <div class="box">
            <div class="flex-col">
              <p>FP Value of Gen1</p>
              <h1>1.00 sol</h1>
            </div>
          </div>

          <div class="box">
            <div class="flex-col">
              <p>Total Value of Gen1</p>
              <h1>10.00 sol</h1>
            </div>
          </div>
        </div>
            
            <Tabs_g1 bind:activeTabValue={currentTab_g} items={tabItems_g} />

            <!-- Gen1 Stake Content -->  
            {#if 1 === currentTab_g}          
            <div class=" text-lg sm:text-2xl font-mono font-bold py-5 tracking-wider">
            {TITLE}
            </div>
            <div class="text-sm sm:text-md font-semibold pb-5 text-gray-600 ">
              {DESCRTIPTION}
            </div>
            <h3>Gen1 unStaked content</h3>
            <div class="flex flex-wrap space-evenly space-evenly">
              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://www.arweave.net/DhPNIq6ws07sG5xVdR3c5DpdLpXDTlf0Jq0wKMkxteg?ext=png" alt="RC_2576" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>
              
              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center">
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>



            </div>
            {/if}
             <!-- End Gen1 Stake Content -->   

            <!-- Gen1 unStake Content -->  
            {#if 2 === currentTab_g}          
            <div class=" text-lg sm:text-2xl font-mono font-bold py-5 tracking-wider">
            {TITLE}
            </div>
            <div class="text-sm sm:text-md font-semibold pb-5 text-gray-600 ">
              {DESCRTIPTION}
            </div>
            <h3>Gen1 Staked content</h3>
            <div class="flex flex-wrap space-evenly">
              <div class="card flex flex-col p-1 justify-center" >
                <p class="flex-1">
                  <img src="https://www.arweave.net/DhPNIq6ws07sG5xVdR3c5DpdLpXDTlf0Jq0wKMkxteg?ext=png" alt="RC_2576" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button">Stake</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center" >
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button">Stake</button>
                </div>
              </div>
            </div>
            {/if}
             <!-- End Gen1 unStake Content -->   


        {/if}
        <!-- End Gen1 Content -->   



        <!-- Gen2 Content -->    
        {#if 2 === currentTab}
        <div class="flex justify-around mb-10" data-v-9aebbff6="">
          <div class="box">
              <div class="flex-col">
                <p>Gen2 Cocks staked</p>
                <h1>0</h1>
              </div>
          </div>
          <div class="box">
              <div class="flex-col">
                <p>% Gen2 Cocks staked</p>
                <h1>0%</h1>
              </div>
          </div>
        </div>

        <div class="flex justify-around mb-10" data-v-9aebbff6="">
          <div class="box">
            <div class="flex-col">
              <p>FP Value of Gen2</p>
              <h1>1.00 sol</h1>
            </div>
          </div>

          <div class="box">
            <div class="flex-col">
              <p>Total Value of Gen2</p>
              <h1>10.00 sol</h1>
            </div>
          </div>
        </div>
            
            <Tabs_g1 bind:activeTabValue={currentTab_g} items={tabItems_g} />

            <!-- Gen2 Stake Content -->  
            {#if 1 === currentTab_g}          
            <div class=" text-lg sm:text-2xl font-mono font-bold py-5 tracking-wider">
            {TITLE}
            </div>
            <div class="text-sm sm:text-md font-semibold pb-5 text-gray-600 ">
              {DESCRTIPTION}
            </div>
            <h3>Gen2 unStaked content</h3>
            <div class="flex flex-wrap space-evenly">
              <div class="card flex flex-col p-1 justify-center" >
                <p class="flex-1">
                  <img src="https://www.arweave.net/DhPNIq6ws07sG5xVdR3c5DpdLpXDTlf0Jq0wKMkxteg?ext=png" alt="RC_2576" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>

              <div class="card flex flex-col p-1 justify-center" >
                <p class="flex-1">
                  <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                </p>
                <div class="mt-2">
                  <p style="text-align: left">
                    RC_2576
                  </p>
                </div>

                <div class="mt-2 mb-2">
                  <p style="text-align: left">
                    RATE: 5 $RICE/DAY
                  </p>
                </div>

                <div class="mt-2 mb-6" style="text-align: left">
                  <button class="big-button2">unStaked</button>
                </div>
              </div>
            </div>
            {/if}
             <!-- End Gen2 Stake Content -->   

            <!-- Gen2 unStake Content -->  
            {#if 2 === currentTab_g}          
            <div class=" text-lg sm:text-2xl font-mono font-bold py-5 tracking-wider">
              {TITLE}
              </div>
              <div class="text-sm sm:text-md font-semibold pb-5 text-gray-600 ">
                {DESCRTIPTION}
              </div>
              <h3>Gen2 Stake content</h3>
              <div class="flex flex-wrap space-evenly">
                <div class="card flex flex-col p-1 justify-center" >
                  <p class="flex-1">
                    <img src="https://www.arweave.net/DhPNIq6ws07sG5xVdR3c5DpdLpXDTlf0Jq0wKMkxteg?ext=png" alt="RC_2576" data-v-3ca34397="">
                  </p>
                  <div class="mt-2">
                    <p style="text-align: left">
                      RC_2576
                    </p>
                  </div>
  
                  <div class="mt-2 mb-2">
                    <p style="text-align: left">
                      RATE: 5 $RICE/DAY
                    </p>
                  </div>
  
                  <div class="mt-2 mb-6" style="text-align: left">
                    <button class="big-button">Stake</button>
                  </div>
                </div>
  
                <div class="card flex flex-col p-1 justify-center" >
                  <p class="flex-1">
                    <img src="https://arweave.net/h9ZLrzUCGmp05fRQUhKj9YzNf7FwUtxDeOPMi3Fd3lQ" alt="RC_462" data-v-3ca34397="">
                  </p>
                  <div class="mt-2">
                    <p style="text-align: left">
                      RC_2576
                    </p>
                  </div>
  
                  <div class="mt-2 mb-2">
                    <p style="text-align: left">
                      RATE: 5 $RICE/DAY
                    </p>
                  </div>
  
                  <div class="mt-2 mb-6" style="text-align: left">
                    <button class="big-button">Stake</button>
                  </div>
                </div>

              </div>
            {/if}
             <!-- End Gen2 unStake Content -->   


        {/if}
        <!-- End Gen2 Content -->   
        

      </div>
    </div>
  </main>

