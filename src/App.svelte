<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Max";
  let title = "";
  let image = "";
  let description = "";
  let formState = "empty";

  let createdContacts = [];

  function addContact(){
    if(
            name.trim().length == 0 ||
            title.trim().length == 0 ||
            image.trim().length == 0 ||
            description.trim().length == 0
    ){
      formState = 'invalid';
      return;
    }
    createdContacts =[...createdContacts, {
      id: Math.random();
      name: name,
      jobTitle: title,
      imageURL: image,
      desc: description
    }];
    formState = 'done';
  }
  function deleteFirst(){
    createdContacts = createdContacts.slice(1);
  }
  function deleteLast(){
    createdContacts = createdContacts.slice(0, -1)
  }
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" />
  </div>
</div>

<button on:click={addContact}>Add Contact Card</button>
<button on:click={deleteFirst}>Delete First</button>
<button on:click={deleteLast}>Delete Last</button>

{#if formState == 'invalid'}
  <p>Card is incomplete</p>
{/if}
{#each createdContacts as contact, index (contact.id)}
  <h2>{index}</h2>
  <ContactCard
          userName={contact.name}
          jobTitle={contact.jobTitle}
          description={contact.desc}
          userImage={contact.imageURL}
  />
  {:else}
  <p>Let's enter some contacts</p>
  {/each}