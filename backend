const express = require('express');
const bodyParser = require('body-parser');
const cors = require('cors');

const app = express();
const port = 3000;

// Middleware
app.use(cors());
app.use(bodyParser.json());

// In-memory storage (replace with a real database later)
let users = {
  'user1': { userId: 'user1', qrCodes: [] }
};

// GET /api/user - Fetch user data
app.get('/api/user', (req, res) => {
  const userId = 'user1'; // Hardcoded user ID for now
  const user = users[userId];
  if (user) {
    res.json(user);
  } else {
    res.status(404).json({ error: 'User not found' });
  }
});

// POST /api/qrcode - Add a new QR code
app.post('/api/qrcode', (req, res) => {
  const { userId, qrCode } = req.body;
  if (users[userId]) {
    users[userId].qrCodes.push(qrCode);
    res.status(201).json({ message: 'QR code added successfully' });
  } else {
    res.status(404).json({ error: 'User not found' });
  }
});

// Start server
app.listen(port, () => {
  console.log(`QR Keychain backend running at http://localhost:${port}`);
});
