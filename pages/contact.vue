<template>
    <div id="cards">
        <div class="text">
            <h1>Contact me</h1>
            <div class="sous-text">
            <h2>by :</h2>
        </div>
        </div>
        <a class="card" href="mailto:marlon.pegahi@epitech.eu">
            <div class="card-content">
                <div class="image">
                    <img src="~/assets/mail.png" alt=""/>
                </div>
                <div class="text">
                    <h4>Mail</h4>
                </div>
            </div>
        </a>
        <a class="card" href="https://discordapp.com/users/952861093095690300" target="blank">
            <div class="card-content">
                <div class="image">
                    <img src="~/assets/real_realdiscord.png" alt=""/>
                </div>
                <div class="text">
                    <h4>Discord</h4>
                </div>
            </div>
        </a>
        <a class="card" href="https://github.com/Marlon830" target="blank">
            <div class="card-content">
                <div class="image">
                    <img src="~/assets/image.png" alt=""/>
                </div>
                <div class="text">
                    <h4>Github</h4>
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