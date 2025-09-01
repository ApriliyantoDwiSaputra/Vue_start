<template>
    <main class="about-page">
        <div class="container">
            <div class="member">
                <img src="https://i.pinimg.com/736x/d0/e9/8c/d0e98c7182a9cedd410c77f95ec8cabc.jpg" alt="image">
                <h1>Sarah Amilia</h1>
                <p>UI/UX Designer with a passion for creating intuitive and engaging user experiences. Focused on modern, clean, and user-friendly interfaces.</p>
                <button>View Details</button>
            </div>
            <div class="member">
                <img src="https://i.pinimg.com/736x/10/e3/8c/10e38c9ad5680531b1485052cacc4f5d.jpg" alt="image">
                <h1>Michael Lee</h1>
                <p>Full-Stack Developer experienced in building scalable web applications. Skilled in JavaScript, Vue.js, Laravel, and cloud deployment.</p>
                <button>View Details</button>
            </div>
            <div class="member">
                <img src="https://i.pinimg.com/736x/e3/9b/b7/e39bb75dfc09441cebafb6bb197ff6bf.jpg" alt="image">
                <h1>Emylia Carter</h1>
                <p>Project Manager ensuring smooth collaboration between teams. Strong background in agile methodologies and product strategy.</p>
                <button>View Details</button>
            </div>
        </div>
    </main>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.container {
    display: flex;
    height: 100%;
    gap: 1rem;
    color: var(--light);
    background-color: var(--dark-alt);
    padding: 1rem;
    border-radius: 6px;
    
    .member {
        flex: 1;
        border-radius: 6px;
        text-align: center;
        padding: 1.5rem;
        margin-top: 3rem;
        
        img {
            display: block;
            margin: 0 auto 1rem auto;
            border-radius: 50%;
            width: 150px;
            height: 150px;
            object-fit: cover;
            object-position: center;
            align-items: center;
        }

        h1 {
            color: var(--light);
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }

        p {
            color: var(--light);
            font-size: 1rem;
            margin-bottom: 1rem;
        }

        button {
            padding: 0.5rem 1rem;
            background-color: var(--primary);
            color: var(--dark);
            font-weight: 600;
            border-radius: 4px;
            transition: background-color 0.3s ease;

            &:hover {
                background-color: var(--primary-alt);
            }
        }
    }

}
</style>