<script>
    import { fly } from "svelte/transition";
    import { writable } from "svelte/store";

    let flipped = false;
</script>

<div class="profile-image-container">
    <div class="flip-container {flipped ? 'flipped' : ''}">
        <img
            src="https://alantaijournal.weebly.com/uploads/1/4/0/0/140039658/dsc00908-900x600-4_orig.jpg"
            alt="Profile"
            class="front"
            style="width: 300px; height: 200px; border-radius: 50%;"
        />
        <div class="back" style="background-color: #fff; border-radius: 50%;">
            <!-- Add your app icons and links here -->
            <a
                href="https://twitter.com"
                target="_blank"
                rel="noopener noreferrer"
            >
                <img
                    src="/images/twitter-icon.png"
                    alt="Twitter"
                    width="48"
                    height="48"
                />
            </a>
            <a
                href="https://linkedin.com"
                target="_blank"
                rel="noopener noreferrer"
            >
                <img
                    src="/images/linkedin-icon.png"
                    alt="LinkedIn"
                    width="48"
                    height="48"
                />
            </a>
        </div>
    </div>
</div>

<style>
    .profile-image-container {
        perspective: 1000px;
        position: relative;
        display: inline-block;
        animation: floating 3s ease-in-out infinite;
        width: 300px;
        height: 200px;
        border-radius: 50%;
        margin-top: 3rem;
    }

    .profile-image-container::before {
        content: "";
        display: block;
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.2);
        border-radius: 50%;
        z-index: -1;
        transform: translateY(10px);
    }

    @keyframes floating {
        0% {
            transform: translateY(0px);
        }
        50% {
            transform: translateY(-20px);
        }
        100% {
            transform: translateY(0px);
        }
    }

    .profile-image-container:hover .flip-container .front {
        transform: rotateY(180deg);
    }

    .profile-image-container:hover .flip-container .back {
        transform: rotateY(0deg);
    }

    .front,
    .back {
        backface-visibility: hidden;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        transition: transform 0.6s;
    }

    .front {
        z-index: 2;
        box-shadow: 0 0 10px #00ff00, 0 0 20px #00ff00, 0 0 30px #00ff00,
            0 0 40px #00ff00;
    }

    .back {
        transform: rotateY(180deg);
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
</style>
