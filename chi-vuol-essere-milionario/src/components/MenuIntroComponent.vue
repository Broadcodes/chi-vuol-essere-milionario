<template>
    <div class="container">
        <video id="videoSfondo" src="@/../public/video/Menu.mp4" loop muted autoplay></video>
        <div class="containerMenu">
            <div id="audio">
                <div class="audio-btn">
                    <i class="fa-solid fa-volume-high"></i>
                </div>
                <div class="controller-audio">
                    <audio controls autoplay loop>
                        <source src="@/../public/audio/menu.mp3" type="audio/mp3">
                    </audio>
                </div>
            </div>

            <div class="logo" :class="{ 'view': this.viewImageLogo }">
                <img src="@/../public/image/logo.png" alt="logo - chi vuol essere milionario?">
            </div>
            <div class="textMenu" :class="{ 'view': this.viewImageLogo }">
                <h1>Pronto ad affrontare la scalata verso il milione?</h1>
            </div>
            <div class="menu" :class="{ 'view': this.viewButtonPlay }">
                <img :src=this.buttonPlay alt="Nuova Partita">
                <h2 @mouseover="changeColor" @mouseout="changeColor" @click="$emit('newGame', true)">NUOVA PARTITA</h2>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MenuIntroComponent',
    data() {
        return {
            viewImageLogo: false,
            viewButtonPlay: false,
            isButtonPlay: false,
            buttonPlay: '/image/areaRisposta.png',
        }
    },
    methods: {
        changeColor() {
            if (this.isButtonPlay) {
                this.buttonPlay = '/image/areaRisposta.png';
                this.isButtonPlay = false;
            } else {
                this.buttonPlay = '/image/areaRispostaAccesa.png';
                this.isButtonPlay = true;
            }
        }
    },
    created() {
        setTimeout(() => {
            this.viewImageLogo = true;
        }, 1000);

        setTimeout(() => {
            this.viewButtonPlay = true;
        }, 2000);


    },
    mounted() {
        let audio = document.querySelector('.audio-btn');
        let controlletAudio = document.querySelector('.controller-audio');
        audio.addEventListener('mouseenter', function () {
            audio.style.display = "none";
            controlletAudio.style.display = "block";
        });

        controlletAudio.addEventListener('mouseleave', function () {

            setTimeout(() => {
                audio.style.display = "block";
                controlletAudio.style.display = "none";
            }, 1000);
        });
    }
}
</script>

<style lang="scss" scoped>
.container {
    width: 100%;
    height: 100vh;
    overflow: hidden;
    position: relative;

    #videoSfondo {
        position: absolute;
        width: 100%;
        height: 100%;
        object-fit: cover;
        opacity: 0.8;
        filter: blur(5px);
        transform: scale(1.01);
    }

    .containerMenu {
        position: relative;

        #audio {
            position: absolute;
            top: 30px;
            right: 30px;
            color: rgb(40, 42, 44);

            .audio-btn {
                padding: 18px;
                border-radius: 50%;
                background-color: rgba(255, 255, 255, 0.3);
                cursor: pointer;
            }

            .controller-audio {
                display: none;
            }
        }

        .view {
            opacity: 1 !important;
        }

        .logo {
            position: absolute;
            top: 10vh;
            left: 50%;
            transform: translate(-50%);
            width: 20vw;
            height: 20vw;
            opacity: 0;
            transition: opacity 3s;

            img {
                width: 100%;
                height: 100%;
            }
        }

        .textMenu {
            position: absolute;
            width: 100%;
            text-align: center;
            top: 55vh;
            left: 50%;
            transform: translate(-50%);
            padding: 15px;
            background: rgb(31, 31, 31);
            background: radial-gradient(circle, rgba(31, 31, 31, 1) 0%, rgba(255, 255, 255, 0) 75%);
            opacity: 0;
            transition: opacity 3s;

            h1 {
                font-size: 2.8rem;
                color: #fff;
                letter-spacing: 0.3rem;
            }
        }

        .menu {
            position: relative;
            top: 75vh;
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
            height: 100px;
            opacity: 0;
            transition: opacity 2s;

            img {
                transform: scale(2);
            }

            h2 {
                padding: 15px 170px;
                position: absolute;
                top: 50%;
                transform: translateY(-50%);
                color: #fff;
                cursor: pointer;
            }
        }
    }
}
</style>