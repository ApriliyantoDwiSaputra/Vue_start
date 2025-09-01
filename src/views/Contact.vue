<template>
  <main class="about-page">
    <div class="container">
      <!-- Bagian Contact -->
      <form class="address">
        <h1>Contact Page</h1>
        <div class="name">
          <div class="firstName">
            <label for="firstName">First name</label>
            <input type="text" name="firstName" id="firstName" />
          </div>
          <div class="lastName">
            <label for="lastName">Last name</label>
            <input type="text" name="lastName" id="lastName" />
          </div>
        </div>
        <div class="username">
            <label for="username">Username</label>
            <input type="text" name="username" id="username" />
        </div>
        <div class="email">
            <label for="email">Email</label>
            <input type="email" name="email" id="email" />
        </div>
        <div class="message">
            <label for="message">Message</label>
            <textarea name="message" id="message" rows="4"></textarea>
        </div>
        <div class="send">
            <button type="submit">Send</button>
        </div>
      </form>

      <!-- Bagian Notification -->
      <div class="notification">
        <div class="card-header">
          <h1>Notification</h1>
        </div>
        <div class="card" v-for="n in 3" :key="n">
          <div class="card-body">
            <h5 class="title">Card {{ n }}</h5>
            <p class="text">Card long text</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
// tidak ada script khusus
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  gap: 1rem;
  color: var(--light);
  padding: 1rem;

  .address {
    flex: 2;
    background-color: var(--dark-alt);
    border-radius: 6px;
    padding: 1.5rem;

    h1 {
      color: var(--light);
      font-size: 1.5rem;
      font-weight: 700;
      margin-bottom: 1rem;
    }

    .name {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;

      .firstName,
      .lastName {
        display: flex;
        flex-direction: column; // label di atas input
      }

      label {
        margin-bottom: 0.3rem;
        font-size: 0.9rem;
      }

      input {
        padding: 0.5rem;
        border: 1px solid var(--dark);
        border-radius: 4px;
        background: var(--dark);
        color: var(--light);
      }
    }

    .username {
        display: flex;
        flex-direction: column;
        margin-top: 1rem;

        label {
          margin-bottom: 0.3rem;
          font-size: 0.9rem;
        }

        input {
            padding: 0.5rem;
            border: 1px solid var(--dark);
            border-radius: 4px;
            background: var(--dark);
            color: var(--light);
        }
    }

    .email {
        display: flex;
        flex-direction: column;
        margin-top: 1rem;

        label {
            margin-bottom: 0.3rem;
            font-size: 0.9rem;
        }

        input {
            padding: 0.5rem;
            border: 1px solid var(--dark);
            border-radius: 4px;
            background: var(--dark);
            color: var(--light);
        }
    }

    .message {
        display: flex;
        flex-direction: column;
        margin-top: 1rem;

        label {
            margin-bottom: 0.3rem;
            font-size: 0.9rem;
        }

        textarea {
            padding: 0.5rem;
            border: 1px solid var(--dark);
            border-radius: 4px;
            background: var(--dark);
            color: var(--light);
            resize: vertical;
        }
    }

    .send {
        margin-top: 1rem;
        display: flex;
        justify-content: flex-end;
    
        button {
            flex: 1;
            padding: 0.5rem 1rem;
            background-color: var(--primary);
            color: var(--light);
            border-radius: 4px;
            font: 600;

        }
    }
  }

  .notification {
    flex: 1;
    background-color: var(--dark-alt);
    border-radius: 6px;
    overflow: hidden;

    .card-header {
      padding: 1rem;
      border-bottom: 1px solid var(--dark);
      h1 {
        font-size: 1.2rem;
        font-weight: 700;
        margin: 0;
      }
    }

    .card {
      border-bottom: 1px solid var(--dark);
      padding: 1rem;

      &:last-child {
        border-bottom: none;
      }

      .title {
        font-size: 1rem;
        font-weight: 600;
        margin-bottom: 0.3rem;
      }

      .text {
        font-size: 0.85rem;
        color: #aaa;
      }
    }
  }
}
</style>
