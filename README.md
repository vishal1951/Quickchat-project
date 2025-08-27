# Quickchat-project
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SmartChat - Vishal Gupta</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f4f4f9;
    }

    .chat-container {
      width: 350px;
      background: white;
      border-radius: 15px;
      box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
      display: flex;
      flex-direction: column;
      overflow: hidden;
    }

    .chat-header {
      background: #4a90e2;
      color: white;
      text-align: center;
      padding: 12px;
      font-size: 18px;
      font-weight: bold;
    }

    .chat-box {
      flex: 1;
      padding: 10px;
      overflow-y: auto;
    }

    .message {
      margin: 6px 0;
      padding: 8px 12px;
      border-radius: 12px;
      max-width: 80%;
      word-wrap: break-word;
      font-size: 14px;
    }

    .user {
      background: #4a90e2;
      color: white;
      align-self: flex-end;
    }

    .bot {
      background: #e5e5ea;
      color: black;
      align-self: flex-start;
    }

    .chat-input {
      display: flex;
      border-top: 1px solid #ccc;
    }

    .chat-input input {
      flex: 1;
      border: none;
      padding: 12px;
      font-size: 14px;
      outline: none;
    }

    .chat-input button {
      background: #4a90e2;
      color: white;
      border: none;
      padding: 12px 20px;
      cursor: pointer;
      font-size: 14px;
    }

    .chat-input button:hover {
      background: #357ab7;
    }
  </style>
</head>
<body>

  <div class="chat-container">
    <div class="chat-header">SmartChat</div>
    <div class="chat-box" id="chat-box"></div>
    <div class="chat-input">
      <input type="text" id="user-input" placeholder="Type a message...">
      <button onclick="sendMessage()">Send</button>
    </div>
  </div>

  <script>
    const chatBox = document.getElementById("chat-box");
    const userInput = document.getElementById("user-input");

    const replies = [
      "Hi! How are you?",
      "That sounds nice.",
      "Can you tell me more?",
      "Good to hear from you.",
      "Interesting point!",
      "Okay, noted.",
      "Thanks for sharing that.",
      "Alright, got it!"
    ];

    function sendMessage() {
      const text = userInput.value.trim();
      if (text === "") return;

      addMessage(text, "user");
      userInput.value = "";

      setTimeout(() => {
        const reply = replies[Math.floor(Math.random() * replies.length)];
        addMessage(reply, "bot");
      }, 600);
    }

    function addMessage(text, sender) {
      const message = document.createElement("div");
      message.classList.add("message", sender);
      message.textContent = text;
      chatBox.appendChild(message);
      chatBox.scrollTop = chatBox.scrollHeight;
    }
  </script>

</body>
</html>
