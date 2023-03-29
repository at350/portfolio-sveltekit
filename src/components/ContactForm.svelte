<script>
    let name = "";
    let email = "";
    let message = "";

    function handleSubmit() {
        // You can replace this with your desired form handling logic (e.g., sending data to your backend)
        alert(
            `Form submitted:\nName: ${name}\nEmail: ${email}\nMessage: ${message}`
        );
    }
</script>

<form class="contact-form" on:submit|preventDefault={handleSubmit}>
    <div class="form-control">
        <label for="name">Name</label>
        <input type="text" id="name" bind:value={name} required />
    </div>
    <div class="form-control">
        <label for="email">Email</label>
        <input type="email" id="email" bind:value={email} required />
    </div>
    <div class="form-control">
        <label for="message">Message</label>
        <textarea id="message" rows="5" bind:value={message} required />
    </div>
    <button type="submit">Send</button>
</form>

<style>
    .contact-form {
        display: flex;
        flex-direction: column;
        width: 100%;
        max-width: 600px;
    }

    .form-control {
        margin-bottom: 1rem;
    }

    label {
        display: block;
        margin-bottom: 0.5rem;
    }

    input,
    textarea {
        width: 100%;
        padding: 0.5rem;
        border: 1px solid #ccc;
        border-radius: 4px;
        font-size: 1rem;
        outline: none;
    }

    input:focus,
    textarea:focus {
        border-color: #0077cc;
    }

    button {
        padding: 0.5rem 1rem;
        background-color: #0077cc;
        color: #fff;
        border: none;
        border-radius: 4px;
        font-size: 1rem;
        cursor: pointer;
    }

    button:hover {
        background-color: #0055aa;
    }
</style>
