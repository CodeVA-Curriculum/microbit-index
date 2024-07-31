<script lang='ts'>
    import {base} from '$app/paths'
    import { onMount } from 'svelte';
    type Card = {
        title:string,
        short:string,
        link:string,
        img?:string
    }
    let projects:Card[] = [
        {
            title: "Virtual Pet",
            short: "A tamagotchi-like toy creature.",
            link: "https://microbit.org/projects/make-it-code-it/microbit-pet/",
            img: "https://media.licdn.com/dms/image/D4D22AQE0WXt9fX9g6g/feedshare-shrink_800/0/1717742742382?e=2147483647&v=beta&t=t5CebEcQMfVHOoeCAAozzbmpWiqeawZ0-6UlOF_iahU"
        },
        {
            title: "Robotic Octopus",
            short: "A simple animatronic cephalopod using servos to control the creature's arms.",
            link: "https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.instructables.com%2FRobotic-Paper-Octopus-with-Microbit%2F&psig=AOvVaw1Rlm2CuR7Ayt592aAob64A&ust=1722471972585000&source=images&cd=vfe&opi=89978449&ved=0CBQQjhxqFwoTCPCLiqWC0IcDFQAAAAAdAAAAABAJ",
            img: "https://content.instructables.com/FLK/2RKJ/KMM12M29/FLK2RKJKMM12M29.jpg?auto=webp&fit=bounds&frame=1&height=1024&width=1024auto=webp&frame=1&height=150"
        },
        {
            title: "Weather Balloon",
            short: "A weather sensing aircraft recording temperature in the upper atmosphere.",
            link: "https://www.bbc.com/news/technology-35824446.amp",
            img: base + '/balloon-microbit.png'
        },
        {
            title: "3-Note Keyboard",
            short: "A musical instrument that works via conductive tape and wire; when the wire touches the tape, it activates musical notes.",
            link: "https://microbit.slps.tp.edu.tw/courses/csintro/radio/project",
            img: "https://microbit.slps.tp.edu.tw/static/courses/csintro/radio/keyboard-copper-tape.png"
        },
        {
            title: "Natural Disaster Sensor",
            short: "A sensor system measuring seismic activity (motion), wind, and temperature.",
            img: "https://core-electronics.com.au/media/faq/kbase/social-no-text-natural-disaster-sensor-project-microbit.png",
            link: "https://core-electronics.com.au/guides/natural-disaster-sensor-project-for-the-microbit-stem/"
        },
        {
            title: "Automatic Door",
            short: "A miniature-scale automatic door using an ultrasonic sensor and a motor",
            img: "https://www.seeedstudio.com/blog/wp-content/uploads/2023/06/%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_16867301134281.png",
            link: "https://www.yuque.com/tinkergen-help-en/microbit/bitgadget_kit#h3-4-automatic-door"
        },
        {
            title: "Robot Bus",
            short: "A simple two-wheel robot fashioned with recycled material to look like a bus.",
            link: "https://www.hackster.io/gpteacher/microbit-bus-robot-car-025057",
            img: base + "/microbit-bus.png"
        },
        {
            title: "Multi-Micro:Bit Display",
            short: "A long, five-digit display with Micro:Bits configured to communicate with one another to coordinate each screen.",
            link: "https://www.google.com/url?sa=i&url=https%3A%2F%2Fmedium.com%2F%40maddisondavid%2Fbuilding-a-multi-micro-bit-display-31ef484e8bb2&psig=AOvVaw1Rlm2CuR7Ayt592aAob64A&ust=1722471972585000&source=images&cd=vfe&opi=89978449&ved=0CBQQjhxqFwoTCPCLiqWC0IcDFQAAAAAdAAAAABBF",
            img: "https://miro.medium.com/v2/resize:fit:2000/1*B9GAuGawuPaKFruV0nZU6A.jpeg"
        },
        {
            title: "Garden Helper",
            short: "A project with an add-on board allowing you to automate plant care with code.",
            img: "https://static.cytron.io/image/catalog/products/REKABIT/REKABIT-soil-moisture-pump.png",
            link: "https://www.google.com/url?sa=i&url=https%3A%2F%2Fmy.cytron.io%2Fc-miscellaneous%2Fp-rekabit-simplifying-robotics-w-microbit&psig=AOvVaw1Rlm2CuR7Ayt592aAob64A&ust=1722471972585000&source=images&cd=vfe&opi=89978449&ved=0CBQQjhxqFwoTCPCLiqWC0IcDFQAAAAAdAAAAABBP"
        },
        {
            title: "Animal Tracker",
            short: "A proof-of-concept project demonstrating how to track animal movements using the Micro:Bit.",
            img: "https://cdn.sanity.io/images/ajwvhvgo/production/ea6128edefc6c7c98b9a2337d3b9f158b97c22a7-800x400.png?q=95",
            link: "https://microbit.org/projects/make-it-code-it/animal-tracker/"
        }
    ]

    let modalImg = ""
    let modalAlt = ""
    let showModal = false

    function toggle(i:number) {
        if(showModal) {
            showModal = false
            modalAlt = ""
            modalImg = ""
        } else {
            showModal = true
            modalAlt = projects[i].short
            modalImg = projects[i].img ? projects[i].img : "https://bulma.io/assets/images/placeholders/1280x960.png"
        }
    }
</script>

<section class='section content'>
    <h1 class='title my-5'>Micro:Bit Project Index</h1>
    <p class='subtitle'>A curated set of Micro:Bit projects for interested teachers & learners.</p>
</section>

<section class='section'>
    {#each projects as project, i}
    <div class="card">
        <div class="card-image">
            <a on:click={() => toggle(i)}>
                <figure class="image">
                <img
                    src={project.img? project.img : 'https://bulma.io/assets/images/placeholders/1280x960.png'}
                    alt="Placeholder"
                />
                </figure>
            </a>
        </div>
        <div class="card-content">
            <div class="media">
                <div class="media-content">
                    <p class="title is-4">{project.title}</p>
                    <p class="subtitle is-6">{project.short}</p>
                </div>
            </div>
        </div>
        <footer class="card-footer">
            <a href="{project.link}" target="_blank" class="card-footer-item">Read More</a>
        </footer>
    </div>
    {/each}
    <div class="modal {showModal? 'is-active' : ''}">
        <div class="modal-background"></div>
        <div class="modal-content">
            <p class="image">
            <img src={modalImg} alt={modalAlt}>
            </p>
        </div>
        <button on:click={() => toggle(0)} class="modal-close is-large" aria-label="close"></button>
    </div>
</section>

<!-- <style>
    .card-footer-item {
        background-color: blue;
    }
</style> -->