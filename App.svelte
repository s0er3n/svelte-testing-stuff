<script>
  import Newsletter from "./Newsletter.svelte";

  const newsletterQuery = `
                                          query Newsletter{
                                            fetchNewsletters(newsletterId: "", userId: "123") {
                                              id
                                              userId
                                              blocks {
                                                count
                                                flairs
                                                upvoteRatio
                                                subreddit
                                              }
                                              options {
                                                frequenzy
                                                time
                                              }
                                            }
                                          }`;

  let url = "00acfd7858f1.ngrok.io/graphql";
  fetch(url, {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: {
      query: newsletterQuery
    }
  })
    .then(res => res.json())
    .then(result => console.log(result));

  let newsletterliste = [
    {
      id: "123",
      userId: "4321",
      blocks: [
        {
          count: 12,
          flairs: ["DD", "News"],
          upvoteRatio: 0.12,
          subreddit: "Finanzen"
        }
      ],
      options: {
        frequenzy: 3,
        time: "04:20"
      }
    },
    {
      id: "123",
      userId: "4321",
      blocks: [
        {
          count: 12,
          flairs: ["DD", "News"],
          upvoteRatio: 0.12,
          subreddit: "Finanzen"
        },
        {
          count: 5,
          flairs: ["DD", "News"],
          upvoteRatio: 0.75,
          subreddit: "MSW"
        }
      ],
      options: {
        frequenzy: 3,
        time: "04:20"
      }
    }
  ];
</script>

<style>
  main {
    font-family: sans-serif;
    text-align: center;
  }
</style>

<main>
	<h1>Fomo Alert</h1>
{#each newsletterliste as newsletter}
	<Newsletter  data={newsletter}/>
{/each}



</main>
