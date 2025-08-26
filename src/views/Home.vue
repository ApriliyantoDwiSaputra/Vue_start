<script setup>
import vueLogo from '../assets/vue.svg'
</script>

<template>
    <div class="home-page">
        <div class="container">
            <div class="hero">
                <div class="text">
                    <h1>The Progressive JavaScript Framework</h1>
                    <p>Quickly design and customize responsive mobile-first sites with Bootstrap, the world’s most popular front-end open source toolkit, featuring Sass variables and mixins, responsive grid system, extensive prebuilt components, and powerful JavaScript plugins.</p>

                    <div class="tombol">
                        <button class="btn">Get Started</button>
                        <button class="btn">Learn More</button>
                    </div>    
                </div>

                <div class="img">
                    <motion 
                    :initial="{ opacity: 0, scale: 0.3, rotate: -180 }"
                    :enter="{ opacity: 1, scale: 1, rotate: 0, transition: { type: 'spring', stiffness: 150, damping: 10 } }"
                    :hover="{ scale: 1.1, rotate: 10, transition: { type: 'spring', stiffness: 200, damping: 12 } }"
                    >
                    <img class="logo" :src="vueLogo" alt="Vue Logo" />
                    </motion>
                </div>
                
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.container {
    padding: 2rem;
}

.hero {
    height: 90vh;
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-items: center;
    background-color: var(--dark-alt);
    padding: 2rem;
    margin-left: 0.5rem;

    .text {
        width: 50%;

        h1 {
            font-size: 2rem;
            font-weight: 900;
            color: var(--light);
            margin-bottom: 1rem;
        }

        p {
            font-size: 1rem;
            font-weight: 400;
            line-height: 1.5rem;
            color: var(--light);
        }

        .tombol {
            margin-top: 2rem;
            border-radius: 0.5rem;

            .btn {
                background-color: var(--primary);
                color: var(--dark);
                margin-right: 1rem;
                padding: 0.75rem 1.5rem;
                font-size: 1rem;
                border-radius: 0.5rem;
                font-weight: 600;
            }
        }
    }

    .img {
        .logo {
            width: 250px;
            height: auto;
        }
    }
}
</style>