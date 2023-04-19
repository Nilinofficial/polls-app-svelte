<script>
    import AddNewPoll from "./components/AddNewPoll.svelte";
import CurrentPolls from "./components/CurrentPolls.svelte";
import Footer from "./components/Footer.svelte";
import Header from "./components/Header.svelte";
    import Tabs from "./shared/Tabs.svelte";

// tabs
let items = ['Current Polls', 'Add New Poll'];
let activeItem = 'Current Polls';

const tabChange = (e) => {
 activeItem = e.detail;
}

let polls = [
    {
        id:1,
        question:" fav programming language?",
        answerA : "Javascript",
        answerB:"Python",
        votesA:5,
        votesB:2
    }
]


const handleAdd= (e) => {
     const poll = e.detail;
     polls = [poll, ...polls]
     console.log(polls);
     activeItem = 'Current Polls';
}

const handleVote = (e) => {
  const {option,id}  =  e.detail
  let copiedPolls = [...polls];
    let upvotedPoll= copiedPolls.find((poll) => poll.id === id)

    if(option === 'a') {
        upvotedPoll.votesA++
    }
    if(option === 'b') {
        upvotedPoll.votesB++
    }

    polls = copiedPolls
}

</script>
<Header/> 

<main>
<Tabs {items} {activeItem} on:tabChange={tabChange}/>
 
{#if activeItem === 'Current Polls' } 
	<CurrentPolls {polls} on:vote={handleVote} />

{:else if activeItem === "Add New Poll"}
   <AddNewPoll on:add={handleAdd}/>
{/if}
</main>
<Footer/>



<style>
main {
	
	max-width: 960px;
	margin: 40px auto ;

}
</style>