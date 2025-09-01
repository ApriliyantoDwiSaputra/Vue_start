<template>
    <main class="about-page">
        <div class="judul">
            <h1>System settings</h1>
            <p>Please enable system alert you will get.</p>
        </div>

        <div class="container">
            <div class="card">
                <div class="card-body">
                    <div class="text">
                        <span>Notify me about new features and updates</span>
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                    </div>
                    <div class="toggle">
                        <input type="checkbox" checked>
                    </div>
                </div>
                <div class="card-body">
                    <div class="text">
                        <span>Notify me by email for latest news</span>
                        <p>Nulla et tincidunt sapien. Sed eleifend volutpat elementum.</p>
                    </div>
                    <div class="toggle">
                        <input type="checkbox" checked>
                    </div>
                </div>
                <div class="card-body">
                    <div class="text">
                        <span>Notify me about tips on using account</span>
                        <p>Donec in quam sed urna bibendum tincidunt quis mollis mauris.</p>
                    </div>
                    <div class="toggle">
                        <input type="checkbox" checked>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="judul">
            <h1>Security settings</h1>
            <p>Control security alert you will be notified.</p>
        </div>

        <div class="container">
            <div class="card">
                <div class="card-body">
                    <div class="text">
                        <span>Unusual activity notifications</span>
                        <p>Donec in quam sed urna bibendum tincidunt quis mollis mauris.</p>
                    </div>
                    <div class="toggle">
                        <input type="checkbox" checked>
                    </div>
                </div>
                <div class="card-body">
                    <div class="text">
                        <span>Unauthorized financial activity</span>
                        <p>Fusce lacinia elementum eros, sed vulputate urna eleifend nec.</p>
                    </div>
                    <div class="toggle">
                        <input type="checkbox" checked>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<script setup>

</script>

<style lang="scss" scoped>
main {
    padding: 1rem 5rem;
    color: var(--dark-alt);
    
    h1 {
        font-size: 2rem;
        font-weight: 600;
    }
}

.container {
    margin: 0.5rem 2rem;
    width: 90%;
    background-color: var(--dark-alt);
    color: var(--light);
    padding: 1rem;
    border-radius: 6px;
}

.card {
    width: 100%;
}

.card-body {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem;
    border-bottom: 1px solid var(--dark);

    &:last-child {
        border-bottom: none;
    }

    .text {
        span {
            font-size: 1rem;
            font-weight: 600;
        }

        p {
            font-size: 0.85rem;
            color: #aaa;
            margin-top: 0.3rem;
        }
    }
}

.toggle {
    input {
        font-size: 5rem;
        width: 3rem;
        height: 1.5rem;
        accent-color: var(--primary);
    }
}
</style>