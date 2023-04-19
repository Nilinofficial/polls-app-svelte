<script>
    import Button from "../shared/Button.svelte";
    import { createEventDispatcher } from "svelte";

let fields = {question:"",answerA:"",answerB:""};
let errors = {question:"",answerA:"",answerB:""};
let valid = false;

let dispatch = createEventDispatcher();

const submitHandler = () => {
    valid = true
    //validate question 
  if(fields.question.trim().length <5) {
    valid = false;
      errors.question = "Question must be atleast 5 characters long";
 
    }
    else {
        errors.question = ""
    }

    // validate answer one

    if(fields.answerA.trim().length <1) {
    valid = false;
      errors.answerA = "answerA cannot be empty";
 
    }
    else {
        errors.answerA = ""
    }

    // validate answer two 

    if(fields.answerB.trim().length<1) {
    valid = false;
      errors.answerB = "answerB cannot be empty";
 
    }
    else {
        errors.answerB = ""
    }

 if(valid) {
   let poll = {...fields,votesA:0,votesB:0,id:Math.random()}
   dispatch('add',poll) 
}


}



</script>

<form on:submit|preventDefault={submitHandler} >

    <div class="form-field">
        <label for="question">Poll Question</label>
        <input
        bind:value={fields.question}
        type="text" id="question">
        <div class="errors">
            {errors?.question}
        </div>
    </div>

    <div class="form-field">
        <label for="answer-a">Answer A</label>
        <input type="text" id="answer-a"
        bind:value={fields.answerA}
        >
        <div class="errors">
            {errors?.answerA}
        </div>
    </div>

    <div class="form-field">
        <label for="answer-b">Answer B</label>
        <input type="text" id="answer-b"
        bind:value={fields.answerB}
        >
        <div class="errors">
            {errors?.answerB}
        </div>
    </div>

      <Button type="secondary">
        Add Poll
      </Button>
</form>


<style>
    
    form {
       
        width: 400px;
        margin: 0 auto;
        text-align: center;
    }

    @media screen and (max-width: 900px) {
        form {
       
       width: 300px;
       margin: 0 auto;
       text-align: center;
   }

}

    .form-field {
        margin: 18px auto;
    }

input {
  width: 100%;
  border-radius: 6px;
}

label {
    margin: 10px auto;
    text-align: left;
}
.errors {
    color:red;
    font-size: small;
    display: flex;
    align-items: start;
}

</style>