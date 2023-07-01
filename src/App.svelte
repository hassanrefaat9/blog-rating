<script>
   import FeedbackForm from "./components/FeedbackForm.svelte";
  import FeedbackList from "./components/FeedbackList.svelte";
   import FeedbackStats from "./components/FeedbackStats.svelte";

  let feedback = [
    {
      id: 1,
      rating: 10,
      text: "This is a great app!, i am happy with that"
    },
    {
      id: 2,
      rating: 5,
      text: "This is a great app!, i am happy with that"
    },
    {
      id: 3,
      rating: 8,
      text: "This is a great app!, i am happy with that"
    },
    {
      id: 4,
      rating: 8,
      text: "lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla euismod, nisl quis tincidunt ultricies, nunc nisl ultricies nunc, nec aliquam nisl"
    }
  ]

  $: count = feedback.length
  $: average = feedback.reduce((acc, item) => acc + item.rating, 0) / feedback.length

const deleteFeedback =(e) =>{
  const itemId = e.detail
  feedback = feedback.filter((item) => item.id !== itemId)
}
</script>

<main class="container">
  <FeedbackForm/>
  <FeedbackStats {count} {average}/>
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback}/>


  </main>

<style>
  
</style>
