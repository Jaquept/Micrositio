# Micrositio
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Micrositio con Chat</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js"></script>
    <style>
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: #333;
        }

        .container {
            width: 450px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            text-align: center;
        }

        .welcome-img {
            width: 100%;
            border-radius: 15px;
            margin-bottom: 20px;
        }

        h1 {
            font-size: 2em;
            margin-bottom: 20px;
        }

        #chat-box {
            border: 2px solid #ff9a9e;
            padding: 10px;
            border-radius: 10px;
            margin-bottom: 20px;
            height: 300px;
            overflow-y: auto;
            background: #fff;
        }

        #message-input {
            width: calc(100% - 90px);
            padding: 10px;
            border: 2px solid #ff9a9e;
            border-radius: 10px;
            font-size: 16px;
            margin-right: 10px;
        }

        #send-btn {
            padding: 10px 20px;
            background-color: #ff6f61;
            color: #fff;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        #send-btn:hover {
            background-color: #e55550;
        }

        .encrypted-message {
            font-style: italic;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <br>
        <br>
        <img src="https://i.pinimg.com/564x/e9/c3/bb/e9c3bb65cac1c256ca126fcd6780bb91.jpg" alt="Welcome Image" class="welcome-img">
        <h1>Bienvenido al chat</h1>
        <div id="chat-box">
            <div id="chat"></div>
        </div>
        <input type="text" id="message-input" placeholder="Escribe tu mensaje...">
        <button id="send-btn">Enviar</button>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const chatBox = document.getElementById('chat');
            const messageInput = document.getElementById('message-input');
            const sendButton = document.getElementById('send-btn');

            sendButton.addEventListener('click', function() {
                const message = messageInput.value.trim();
                if (message !== '') {
                    const encryptedMessage = encryptMessage(message);
                    appendMessage('Jaqueline', encryptedMessage);
                    messageInput.value = '';
                    // Aquí puedes agregar la lógica para enviar el mensaje al servidor o procesarlo de otra manera
                }
            });

            function encryptMessage(message) {
                // Clave de cifrado (debes mantener esto seguro y enviarla al destinatario de manera segura)
                const key = 'Chikis12345678';
                // Cifrar el mensaje con AES utilizando la clave
                const encrypted = CryptoJS.AES.encrypt(message, key).toString();
                return encrypted;
            }

            function appendMessage(sender, message) {
                const messageElement = document.createElement('div');
                messageElement.innerHTML = `<strong>${sender}:</strong> <span class="encrypted-message">${message} (Mensaje cifrado)</span>`;
                chatBox.appendChild(messageElement);
                chatBox.scrollTop = chatBox.scrollHeight;
            }
        });
    </script>
</body>
</html>
