<script>
  import { nativeCurrencyPrice } from "$lib/runes/global.svelte";
  import { createTargetNetwork } from "$lib/runes/targetNetwork.svelte";
  import BuidlGuidlLogo from "./assets/BuidlGuidlLogo.svelte";
  import { CurrencyDollar, Heart, Icon, MagnifyingGlass } from "svelte-hero-icons";
  import { hardhat } from "viem/chains";
  import Faucet from "./scaffold-eth/Faucet.svelte";
  import SwitchTheme from "./SwitchTheme.svelte";

  const targetNetwork = $derived.by(createTargetNetwork());
  const isLocalNetwork = $derived(targetNetwork.id === hardhat.id);
</script>

<div class="mb-11 min-h-0 px-1 py-5 lg:mb-0">
  <div>
    <div class="pointer-events-none fixed bottom-0 left-0 z-10 flex w-full items-center justify-between p-4">
      <div class="pointer-events-auto flex flex-col gap-2 md:flex-row">
        {#if nativeCurrencyPrice.price > 0}
          <div>
            <div class="btn btn-primary btn-sm cursor-auto gap-1 font-normal">
              <Icon src={CurrencyDollar} class="h-4 w-4" />
              <span>{nativeCurrencyPrice.price}</span>
            </div>
          </div>
        {/if}
        {#if isLocalNetwork}
          <Faucet />
          
        {/if}
      </div>
	  <!--
      <SwitchTheme class="pointer-events-auto {isLocalNetwork && 'self-end md:self-auto'}" />
	  -->
    </div>
  </div>
  <div class="w-full">
    <ul class="menu menu-horizontal w-full">
      <div class="flex w-full items-center justify-center gap-2 text-sm">
        <div class="text-center">
        </div>

        <div class="flex items-center justify-center gap-2">
        </div>
   
        <div class="text-center">
        
        </div>
      </div>
    </ul>
  </div>
</div>
