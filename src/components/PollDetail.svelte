<script>
    import Card from "../shared/Card.svelte";
    import {createEventDispatcher} from 'svelte';

    const dispatch = createEventDispatcher();

    export let poll;

    // REACTIVE VALUE

    $: totalVotes = poll.votesA + poll.votesB;
    $:percentA = Math.floor(100/totalVotes *poll.votesA);
    $:percentB = Math.floor(100/totalVotes * poll.votesB)

    const handleVote = (option,id) => {
        dispatch('vote',{option,id})
    }

</script>

<Card>
    <div class="poll">
        <h3>{poll.question}</h3>
        <p>Total votes : {totalVotes}</p>
         <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore missing-declaration -->
        <div class="answer"
        on:click={() => handleVote('a',poll.id)}
        >
            <div class="percent percent-a" style="width:{percentA}%"/>
            <span>{poll.answerA} ({poll.votesA})</span>
        </div>

        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore missing-declaration -->
        <div class="answer"
        on:click={() => handleVote('b',poll.id)}
        >
            <div class="percent percent-b" style="width:{percentB}%"/>
            <span>{poll.answerB} ({poll.votesB})</span>
        </div>
    </div>
</Card>

<style>
    h3 {
        margin: 0 auto;
        color: #555;
    }

    p {
        margin-top: 6px;
        font-size: 14px;
        color: #aaa;
        margin-bottom: 30px;
    }

    .answer {
        background: #fafafa;
        cursor: pointer;
        margin: 10px auto;
        position: relative;
    }

    .percent {
        height: 100%;
        position: absolute;
        box-sizing: border-box;
    }
 .percent-a {
  background: rgba(217, 27, 66, 0.2)
}

    .percent-b{
        background: rgba(69, 196, 150, 0.2)
    }
    .answer:hover {
        opacity: 0.6;
    }

    span {
        display: inline-block;
        padding: 10px 20px;
    }
</style>

