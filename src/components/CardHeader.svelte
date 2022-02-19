<script>
  import { userState } from "../lib/store";
  import { LAMPORTS_PER_SOL } from "@solana/web3.js";
</script>

<div class="justify-end flex p-3">

  <div class="flex">
    {#if !$userState.walletPublicKey}
      <span class="my-auto mr-2 rounded-full h-2 w-2 bg-gray-500" />
      <span class=" my-auto text-gray-600 text-sm"> Not Connected </span>
    {:else}
      <div class=" flex flex-col">
        <div class="flex">
          <span class="my-auto mr-2 rounded-full h-2 w-2 bg-green-500" />
          <span class=" my-auto text-gray-600 text-sm">
            {$userState.walletPublicKey?.slice(0, 8)}
          </span>
        </div>
        <div class=" text-xs text-gray-600 text-right ">
          {($userState?.userBalance / LAMPORTS_PER_SOL).toFixed(2)} SOL
        </div>
      </div>
    {/if}
  </div>
</div>
