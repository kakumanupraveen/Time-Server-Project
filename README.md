# Time-Server-Project
This repository contains the code for a Node.js time server. The time server is a server-side application built with Node.js that responds to HTTP requests with the current date and time in JSON format. 

time-server.js
var net = require('net');

var server = net.createServer(function (socket) {
  var date = new Date();
  var year = date.getFullYear();
  var month = ('0' + (date.getMonth() + 1)).slice(-2);
  var day = ('0' + date.getDate()).slice(-2);
  var hour = (
    '0' + date.getHours()).slice(-2);
  var minute = ('0' + date.getMinutes()).slice(-2);
  var formattedDate = `${year}-${month}-${day} ${hour}:${minute}\n`;

  socket.end(formattedDate);
});

var port = process.argv[2];
server.listen(port);


http-json-api-server.js
var http = require('http');

var server = http.createServer(function (req, res) {
  if (req.url === '/api/currenttime') {
    var date = new Date();
    var jsonResponse = {
      year: date.getFullYear(),
      month: ('0' + (date.getMonth() + 1)).slice(-2),
      date: ('0' + date.getDate()).slice(-2),
      hour: ('0' + date.getHours()).slice(-2),
      minute: ('0' + date.getMinutes()).slice(-2)
    };

    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify(jsonResponse));
  } else {
    res.writeHead(404);
    res.end();
  }
});

server.listen(8000);

google slides:
https://docs.google.com/presentation/d/1DimqJIgVtgZYi5SebVJqVHvtu7E5xSOx_mUhJFbyDU0/edit#slide=id.g273275bba51_0_31
