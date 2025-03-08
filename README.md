# Gbision
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GBI SION Chatbot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
            margin: 0;
        }
        .chat-container {
            width: 90%;
            max-width: 400px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }
        .chat-box {
            height: 300px;
            overflow-y: auto;
            padding: 10px;
            display: flex;
            flex-direction: column;
        }
        .chat-input {
            display: flex;
            padding: 10px;
            border-top: 1px solid #ddd;
            background: white;
        }
        input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            outline: none;
        }
        button {
            padding: 10px;
            border: none;
            background: #007bff;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            margin-left: 5px;
        }
        .message {
            margin: 5px 0;
            padding: 8px;
            border-radius: 5px;
            max-width: 80%;
            word-wrap: break-word;
        }
        .user {
            background: #007bff;
            color: white;
            align-self: flex-end;
        }
        .bot {
            background: #ddd;
            align-self: flex-start;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-box" id="chat-box"></div>
        <div class="chat-input">
            <input type="text" id="user-input" placeholder="Ketik pesan..." onkeypress="handleKeyPress(event)">
            <button onclick="sendMessage()">Kirim</button>
        </div>
    </div>
    
    <script>
        function sendMessage() {
            let inputField = document.getElementById("user-input");
            let message = inputField.value.trim();
            if (message === "") return;
            
            addMessage("user", message);
            inputField.value = "";
            
            setTimeout(() => {
                let response = getBotResponse(message.toLowerCase());
                addMessage("bot", response);
            }, 500);
        }
        
        function getBotResponse(message) {
            if (message.includes("halo") || message.includes("shalom")) {
                return "Shalom jemaat Tuhan yang terkasih, apakah ada yang bisa kami bantu?";
            } else if (message.includes("kapan")) {
                return "Ibadah Minggu Raya GBI SION pukul 10:30 pagi, Sekolah Minggu pukul 07:00 pagi, Ibadah Pemuda Youth pukul 19:00, Ibadah Keluarga akan diumumkan di saat pengumuman ibadah raya.";
            } else if (message.includes("daftar") || message.includes("jemaat")) {
                return "Silahkan kunjungi website kami dan klik pendaftaran.";
            } else if (message.includes("dimana")) {
                return "GBI SION berada di Jalan Danau Toba, Sp4, Gunung Mulya.";
            } else if (message.includes("terimakasih")) {
                return "Sama-sama, sampai jumpa di gereja, Jesus bless you...";
            } else {
                return "Maaf, kami hanya melayani seputar kegerejaan GBI SION.";
            }
        }
        
        function addMessage(sender, text) {
            let chatBox = document.getElementById("chat-box");
            let msgDiv = document.createElement("div");
            msgDiv.classList.add("message", sender);
            msgDiv.textContent = text;
            chatBox.appendChild(msgDiv);
            chatBox.scrollTop = chatBox.scrollHeight;
        }
        
        function handleKeyPress(event) {
            if (event.key === "Enter") {
                sendMessage();
            }
        }
    </script>
</body>
</html>
