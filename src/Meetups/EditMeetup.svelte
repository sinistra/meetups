<script>
  import { createEventDispatcher } from "svelte";
  import TextInput from "../UI/TextInput.svelte";
  import Button from "../UI/Button.svelte";
  import Modal from "../UI/Modal.svelte";

  let title = "";
  let subtitle = "";
  let address = "";
  let imageUrl = "";
  let description = "";
  let email = "";

  const dispatch = createEventDispatcher();

  function submitForm() {
    dispatch("save", {
      title: title,
      subtitle: subtitle,
      address: address,
      imageUrl: imageUrl,
      description: description,
      email: email
    });
  }

  function cancel() {
    dispatch('cancel');
  }
</script>

<style>
  form {
    width: 100%;
  }
</style>

<Modal title="Edit Meetup" on:cancel>
  <form on:submit|preventDefault={submitForm}>
    <TextInput
      type="text"
      id="title"
      label="Title"
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      type="text"
      id="subtitle"
      label="SubTitle"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)} />
    <TextInput
      type="text"
      id="address"
      label="Address"
      value={address}
      on:input={event => (address = event.target.value)} />
    <TextInput
      type="email"
      id="email"
      label="Email"
      value={email}
      on:input={event => (email = event.target.value)} />
    <TextInput
      type="text"
      id="imageUrl"
      label="Image URL"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      id="description"
      controlType="textarea"
      label="Description"
      value={description}
      on:input={event => (description = event.target.value)} />
  </form>
  <div slot="footer">
    <Button type="button" mode="outline" on:click={cancel}>Cancel</Button>
    <Button type="button" on:click={submitForm}>Save</Button>
  </div>
</Modal>
