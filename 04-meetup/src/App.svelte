<script>
    import Header from './UI/Header.svelte';
    import MeetupGrid from './Meetups/MeetupGrid.svelte';
    import TextInput from './UI/TextInput.svelte';
    import Button from './UI/Button.svelte';

    let title="";
    let subtitle="";
    let description="";
    let imageUrl="";
    let address="";
    let contactEmail="";

    //http://cdn.sci-news.com/images/enlarge6/image_7848_1e-Quantum-Reality.jpg

    let meetups = [
        {
            id: 'm1',
            title: 'Coding Bootcamp',
            subtitle: 'Learn to code in 2 hours',
            description: 'In this meetup, we will have some xperts who will teach you coding',
            imageUrl: 'https://techcrunch.com/wp-content/uploads/2015/04/codecode.jpg',
            address: '27th Nerd Road, 32546 New York',
            contactEmail: 'code@test.com'

        },
        {
            id: 'm2',
            title: 'Swim Together',
            subtitle: 'Go swim with Dolphins',
            description: 'Swiming Instruters will tell you the basics',
            imageUrl: 'https://gtimg.tokyo2020.org/image/private/t_article-lead-image-ultrawide/v1582392665/production/ikk26dtn3rv6oo5z17w2',
            address: 'Holiday Inn',
            contactEmail: 'swim@fast.com'

        }
    ];

    function addMeetup() {
        const newMeeetup = {
            id: Math.random().toString(),
            title: title,
            subtitle: subtitle,
            description: description,
            imageUrl: imageUrl,
            address: address,
            contactEmail: contactEmail            
        };

        meetups = [newMeeetup, ...meetups];
    }
</script>
<style>
    main {
        margin-top: 5rem;
    }

    form {
        width: 30rem;
        max-width: 90%;
        margin:auto;
    }
</style>
<Header />

<main>
    <form on:submit|preventDefault="{addMeetup}">
        <TextInput 
            controlType='text' 
            id='title' 
            label='Title' 
            value={title} 
            on:input="{ event => title=event.target.value }"/>
        <TextInput 
            controlType='text' 
            id='subtitle' 
            label='Sub Title' 
            value={subtitle} 
            on:input="{ event => subtitle=event.target.value }"/>
        <TextInput 
            controlType='text' 
            id='address' 
            label='Address' 
            value={address} 
            on:input="{ event => address=event.target.value }"/>
        <TextInput 
            controlType='text' 
            id='imageUrl' 
            label='Image URL' 
            value={imageUrl} 
            on:input="{ event => imageUrl=event.target.value }"/>
        <TextInput 
            controlType='email' 
            id='email' 
            label='Email' 
            value={contactEmail} 
            on:input="{ event => contactEmail=event.target.value }"/>
        <TextInput 
            controlType='textarea' 
            id='description' 
            label='Description' 
            value={description} 
            on:input="{ event => description=event.target.value }"/>
        <Button type="submit" caption="Save" />
    </form>
    <MeetupGrid {meetups}/>
</main>
