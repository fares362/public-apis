// server.js
const express = require('express');
const http = require('http');
const socketIo = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = socketIo(server);

app.get('/', (req, res) => {
    res.sendFile(__dirname + '/index.html');
});

io.on('connection', (socket) => {
    console.log('Un utilisateur est connecté');

    socket.on('chat message', (msg) => {
        console.log('Message reçu: ' + msg);
        // Ici, tu peux intégrer une API de chat comme OpenAI
        // Par exemple :
        // const response = await openAiChatbot(msg);
        // socket.emit('chat message', response);
        socket.emit('chat message', `Réponse à votre question: ${msg}`);
    });

    socket.on('disconnect', () => {
        console.log('Un utilisateur est déconnecté');
    });
});

server.listen(3000, () => {
    console.log('Écoute sur le port 3000');
});
