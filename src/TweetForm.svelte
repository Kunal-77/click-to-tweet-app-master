<script>
	import Help from './shared/Help.svelte';
	import CustomButton from './shared/CustomButton.svelte';
	import CustomInput from './shared/CustomInput.svelte';
	import {copyToClipboard, encodeTweet} from './utils';
	import strings from './strings';
	let text = '';
	let url = '';
	let hashtags = '';
	let username = '';
	let tweet = '';
	
	function clearAll(){
		text = '';
		url = '';
		hashtags = '';
		username = '';
	}
</script>

<style>
    * {
        box-sizing: border-box;
    }
    body {
        background-color: #e0f7fa; /* Light cyan background */
        font-family: 'Arial', sans-serif; /* Use a clean font */
        margin: 0;
        padding: 0;
    }
    .form-container {
        padding: 40px;
        width: 80%;
        max-width: 600px; /* Limit the width for better readability */
        background-color: #ffffff; /* White background for the form */
        border-radius: 15px; /* Rounded corners */
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1); /* Subtle shadow */
        margin: 40px auto; /* Center the container */
        text-align: center; /* Center-align text and inline elements */
    }
    
    .row {
        display: flex; /* Use flexbox for layout */
        align-items: center; /* Center items vertically */
        justify-content: space-between; /* Space between items */
        padding-bottom: 15px; /* Space between rows */
    }

    .form-field {
        color: #00796b; /* Teal color for labels */
        font-size: 18px;
        font-weight: bold;
        flex: 1; /* Allow the label to grow */
        text-align: left; /* Align text to the left */
    }

    .col-one {
        flex: 2; /* Allow input to take more space */
        margin-left: 10px; /* Space between label and input */
    }

    .tooltip {
        padding-left: 5px;
        color: #ff5722; /* Orange color for tooltips */
    }

    .click-container {
        margin-top: 20px; /* Space above buttons */
    }

    /* Button styles */
    button {
        background-color: #00796b; /* Teal button */
        color: white;
        border: none;
        border-radius: 5px; /* Rounded corners */
        padding: 10px 20px; /* Padding for buttons */
        cursor: pointer;
        transition: background-color 0.3s; /* Smooth transition */
        font-size: 16px;
        margin: 5px; /* Space between buttons */
    }

    button:hover {
        background-color: #004d40; /* Darker teal on hover */
    }

    /* Input styles */
    input {
        border: 1px solid #00796b; /* Teal border */
        border-radius: 5px; /* Rounded corners */
        padding: 10px; /* Padding for inputs */
        width: 100%; /* Full width */
        margin-top: 5px; /* Space above input */
        font-size: 16px; /* Font size for inputs */
    }

    input:focus {
        border-color: #004d40; /* Darker teal on focus */
        outline: none; /* Remove default outline */
    }

    /* Responsive layout */
    @media screen and (max-width: 600px) {
        .form-container {
            width: 90%; /* Full width on small screens */
        }
    }
</style>

<div class="form-container">
	<div class="row">
		<span class="form-field">Content</span>
		<CustomInput bind:value={text} placeholder={strings.placeholders.content}/>
		<span class="tooltip"><Help tooltip={strings.contentToolTip}>?</Help></span>
	</div>
	<div class="row">
		<span class="form-field">URL</span>
		<CustomInput bind:value={url} placeholder={strings.placeholders.url}/>
		<span class="tooltip"><Help tooltip={strings.urlToolTip}>?</Help></span>
	</div>
	<div class="row">
		<span class="form-field">Hashtags</span>
		<CustomInput bind:value={hashtags} placeholder={strings.placeholders.hashtags}/>
		<span class="tooltip"><Help tooltip={strings.hashtagsToolTip}>?</Help></span>
	</div>
	<div class="row">
		<span class="form-field">Username</span>
		<CustomInput bind:value={username} placeholder={strings.placeholders.name}/>
		<span class="tooltip"><Help tooltip={strings.usernameToolTip}>?</Help></span>
	</div>
	<div class="click-container">
		<CustomButton onClick={() => tweet = encodeTweet(text, url, hashtags, username)} buttonText="Generate"/>
		<CustomButton onClick={clearAll} buttonText="Clear all"/>
	</div>
	<div>
		<CustomInput type="text" value={tweet} id="myTweet"/>
		<CustomButton onClick={() => copyToClipboard("myTweet")} buttonText="Copy String"/>
	</div>
</div>