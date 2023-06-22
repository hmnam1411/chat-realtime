<template>
    <div class="chat">
        <div class="chat-window">
            <div class="chat-left">
                <div v-if="messages.length == 0">Hãy bắt đầu trò chuyện</div>
                <div v-else>
                    <div class="message" v-for="(item, index) in messages" :key="index">
                        <span class="timestamp">
                            {{ formatDate(item.dateTime) }}
                        </span>
                        <span class="chat-text">
                            {{ item.message }}
                        </span>
                        <div class="sent">
                            {{ getTimeAgo(item.dateTime) }}
                        </div>
                    </div>
                </div>
                <div>
                    <input type="text" v-model="newMessage" @keyup.enter="btnSend()">
                    <button @click="btnSend()">Send</button>
                </div>
            </div>
            <div class="chat-right">

            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            messages: [],

            newMessage: "",

            timeAgo: 0,

            currentTime: new Date()
        }
    },

    computed: {

    },

    created() {
        this.updateCurrentTime(); // Cập nhật thời gian lúc tạo component

        // Cập nhật thời gian sau mỗi giây
        setInterval(() => {
            this.updateCurrentTime();
        }, 1000);
    },

    methods: {
        updateCurrentTime() {
            this.currentTime = new Date();
        },

        formatDate(time) {
            const dateNow = new Date(time)
            const hour = dateNow.getHours()
            const minutes = dateNow.getMinutes()
            const formatTime = `${hour}:${minutes < 10 ? '0' + minutes : minutes}`
            return formatTime
        },

        btnSend() {
            if (this.newMessage) {
                this.messages.push({ id: this.messages.length + 1, message: this.newMessage, dateTime: Date.now() })
                this.newMessage = ''
            }
        },

        getTimeAgo(time) {
            // const now = Date.now()
            const now = this.currentTime.getTime();
            const timeDiff = now - time

            const minutes = Math.floor(timeDiff / 60000)

            // const seconds = Math.floor(timeDiff / 1000); // Số giây trôi qua

            if (minutes > 0) {
                return `Sent ${minutes} minutes ago`
            } else {
                return `Sent recent`
            }


            // if (seconds < 60) {
            //     return `Sent ${seconds} seconds ago`;
            // } else {
            //     const minutes = Math.floor(seconds / 60);
            //     return `Sent ${minutes} minutes ago`;
            // }
        }

    },

    mounted() {
        let timestamp = { seconds: 1549843200, nanoseconds: 0 } // firebase data     
        let myDate = new Date(timestamp.seconds * 1000) // date object

        console.log(myDate)
    },
}
</script>

<style>
.chat-window {
    display: flex;
}

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
</style>