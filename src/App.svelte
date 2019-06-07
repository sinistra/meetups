<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";

  let meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description:
        "In this meetup, we will have some experts that teach you how to code!",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Caffe_Nero_coffee_bar%2C_High_St%2C_Sutton%2C_Surrey%2C_Greater_London.JPG/800px-Caffe_Nero_coffee_bar%2C_High_St%2C_Sutton%2C_Surrey%2C_Greater_London.JPG",
      address: "27th Nerd Road, 32523 New York",
      contactEmail: "code@test.com"
    },
    {
      id: "m2",
      title: "Swim Together",
      subtitle: "Let's go for some swimming",
      description: "We will simply swim some rounds!",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/thumb/6/69/Olympic_swimming_pool_%28Tbilisi%29.jpg/800px-Olympic_swimming_pool_%28Tbilisi%29.jpg",
      address: "27th Nerd Road, 32523 New York",
      contactEmail: "swim@test.com"
    }
  ];

  let title='';
  let subtitle='';
  let address='';
  let imageUrl='';
  let description='';
  let email='';


  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      address: address,
      contactEmail: email,
      imageUrl: imageUrl,
      description: description,
    }

    meetups = [newMeetup, ...meetups];
  }
</script>

<style>
  main {
    padding-top: 4rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />
<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput type="text" id="title" label="Title" value={title} on:input={(event) => (title = event.target.value)} />
    <TextInput type="text" id="subtitle" label="SubTitle" value={subtitle} on:input={(event) => (subtitle = event.target.value)} />
    <TextInput type="text" id="address" label="Address" value={address} on:input={(event) => (address = event.target.value)} />
    <TextInput type="email" id="email" label="Email" value={email} on:input={(event) => (email = event.target.value)} />
    <TextInput type="text" id="imageUrl" label="Image URL" value={imageUrl} on:input={(event) => (imageUrl = event.target.value)} />
    <TextInput id="description" controlType="textarea" label="Description" value={description} on:input={(event) => (description = event.target.value)} />
    <Button type="submit" caption="Save" />
  </form>
  <MeetupGrid {meetups} />
</main>
