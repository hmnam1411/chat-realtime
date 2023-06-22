<!-- <template>
  <div>
    <div class="chat-window">
      <div class="chat-messages">
        <div v-for="message in messages" :key="message.id" class="message">
          <span class="timestamp">{{ formatTimestamp(message.timestamp) }}</span>
          <span class="text">{{ message.text }}</span>
        </div>
      </div>
    </div>
    <div class="input-area">
      <input type="text" v-model="newMessage" @keyup.enter="sendMessage" placeholder="Type your message..." />
      <button @click="sendMessage">Send</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [
        { id: 1, text: "Hello!", timestamp: Date.now() },
        { id: 2, text: "How are you?", timestamp: Date.now() },
        { id: 3, text: "I'm good. Thanks!", timestamp: Date.now() }
      ],
      newMessage: ""
    };
  },
  methods: {
    sendMessage() {
      if (this.newMessage) {
        const newId = this.messages.length + 1;
        this.messages.push({ id: newId, text: this.newMessage, timestamp: Date.now() });
        this.newMessage = "";
      }
    },
    formatTimestamp(timestamp) {
      const date = new Date(timestamp);
      const hours = date.getHours();
      const minutes = date.getMinutes();
      const formattedTime = `${hours}:${minutes < 10 ? '0' + minutes : minutes}`;
      return formattedTime;
    }
  }
};
</script>

<style scoped>
.chat-window {
  height: 300px;
  border: 1px solid #ccc;
  overflow-y: scroll;
}

.message {
  margin-bottom: 10px;
}

.timestamp {
  color: #999;
  font-size: 12px;
}

.text {
  margin-left: 5px;
}

.input-area {
  margin-top: 10px;
}
</style> -->
