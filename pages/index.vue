<template>
    <div id="cards">
        <div class="text">
            <h1>Marlon PEGAHI</h1>
            <div class="sous-text">
            <h2>Student at Epitech</h2>
        </div>
        </div>
        <a class="card" href="about">
            <div class="card-content">
                <div class="image">
                    <img src="~/assets/about.png" alt=""/>
                </div>
                <div class="text">
                    <h4>About me</h4>
                </div>
                <div class="sous-text">
                    <h3>Who am i ?</h3>
                </div>
            </div>
        </a>
        <a class="card" href="portfolio">
            <div class="card-content">
                <div class="image">
                    <img src="~/assets/image.png" alt=""/>
                </div>
                <div class="text">
                    <h4>Github</h4>
                </div>
                <div class="sous-text">
                    <h3>{Portfolio}
                        Want to see what i've done ?</h3>
                </div>
            </div>
        </a>
        <a class="card" href="contact">
            <div class="card-content">
                <div class="image">
                    <img src="~/assets/contact.png" alt=""/>
                </div>
                <div class="text">
                    <h4>Contact</h4>
                </div>
                <div class="sous-text">
                    <h3>Want to contact me ?</h3>
                </div>
            </div>
        </a>
    </div>
</template>

<script setup>
onMounted(async () => {
    const handleOnMouseMove = e => {
        const { currentTarget: target } = e;

        const rect = target.getBoundingClientRect()
        let    x = e.clientX - rect.left
        let    y = e.clientY - rect.top;

        target.style.setProperty("--mouse-x", `${x}px`);
        target.style.setProperty("--mouse-y", `${y}px`);
    }

    for (const card of document.querySelectorAll(".card")) {
        card.onmousemove = e => handleOnMouseMove(e);
    }
})
</script>

<style scoped>
#cards {
    display: flex;
    gap: 8px;
    max-width: 916;
    width: calc(100% - 20px);
}

.card {
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
    cursor: pointer;
    height: 260px;
    position: relative;
    width: 300px;
}

.card:hover::before {
    opacity: 1;
}

.card::before {
    background: radial-gradient(800px circle at var(--mouse-x) var(--mouse-y),
            rgba(255, 255, 255, 0.06),
            transparent 40%);
    border-radius: inherit;
    content: "";
    height: 100%;
    left: 0px;
    opacity: 0;
    position: absolute;
    top: 0px;
    transition: opacity 500ms;
    width: 100%;
    z-index: 2;
}

.card>.card-content {
    background-color: rgb(23, 23, 23);
    border-radius: inherit;
    height: calc(100% - 2px);
    margin: 1px;
    width: calc(100% - 2px);
}

.text {
    color: rgb(214, 205, 205);
    font-family: "Rubik", sans-serif;
    font-weight: 400;
    margin: 0px;
    text-align: center;
}

.sous-text {
    color: rgb(145, 145, 145);
    font-family: "Rubik", sans-serif;
    font-weight: 200;
    font-size: 10px;
    margin: 0px;
    text-align: center;
}

.image {
    width: 200px;
    height: 200px;
    display: flex;
    margin-left: auto;
    margin-right: auto;
}

</style>