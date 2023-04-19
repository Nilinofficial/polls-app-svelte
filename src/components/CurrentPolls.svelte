<script>
    import PollDetail from "./PollDetail.svelte";

export let polls= [];
</script>

<div class="poll-lists">
{#each polls as poll }
    <div>
       <PollDetail {poll} on:vote/>
    </div>
{/each}
</div>


<style>
.poll-lists {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
}

@media screen and (max-width: 700px) {
    .poll-lists {
    display: grid;
    grid-template-columns: 1fr ;
    grid-gap: 20px;
}

 

}
</style>