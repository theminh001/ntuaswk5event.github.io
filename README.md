<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Spectral Quest: Unlock the Stellar Code</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #0b3d91;
      color: white;
      text-align: center;
      padding: 50px;
    }
    h1 {
      font-size: 2.5em;
      margin-bottom: 20px;
    }
    p {
      font-size: 1.2em;
      margin-bottom: 30px;
    }
    input[type="text"] {
      padding: 10px;
      font-size: 1em;
      border: 2px solid #ccc;
      border-radius: 5px;
      width: 300px;
    }
    button {
      padding: 10px 20px;
      font-size: 1em;
      background-color: #ff6f61;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 20px;
    }
    button:hover {
      background-color: #ff4a3d;
    }
    #message {
      margin-top: 20px;
      font-size: 1.2em;
      color: #ffcc00;
    }
  </style>
</head>
<body>
  <h1>Spectral Quest: Unlock the Stellar Code</h1>
  <p>Sort the 15 brightest stars by their spectral classes (OBAFGKM) and enter the password to proceed.</p>
  <p>Password Hint: The password is the sequence of spectral classes from hottest to coolest.</p>
  
  <input type="text" id="password" placeholder="Enter the password">
  <button onclick="checkPassword()">Submit</button>
  
  <p id="message"></p>

  <script>
    // List of the 15 brightest stars and their spectral classes
    const stars = [
      { name: "Sirius", spectralClass: "A1" },
      { name: "Canopus", spectralClass: "F0" },
      { name: "Rigil Kentaurus", spectralClass: "G2" },
      { name: "Arcturus", spectralClass: "K1" },
      { name: "Vega", spectralClass: "A0" },
      { name: "Capella", spectralClass: "G8" },
      { name: "Rigel", spectralClass: "B8" },
      { name: "Procyon", spectralClass: "F5" },
      { name: "Achernar", spectralClass: "B3" },
      { name: "Betelgeuse", spectralClass: "M2" },
      { name: "Hadar", spectralClass: "B1" },
      { name: "Altair", spectralClass: "A7" },
      { name: "Acrux", spectralClass: "B0.5" },
      { name: "Aldebaran", spectralClass: "K5" },
      { name: "Spica", spectralClass: "B1" }
    ];

    // Sort stars by temperature (hottest to coolest)
    const sortedStars = stars.sort((a, b) => {
      const spectralOrder = { O: 0, B: 1, A: 2, F: 3, G: 4, K: 5, M: 6 };
      const aClass = a.spectralClass[0]; // Get the first letter (e.g., "A" from "A1")
      const bClass = b.spectralClass[0];
      return spectralOrder[aClass] - spectralOrder[bClass];
    });

    // Generate the password by combining spectral classes
    const correctPassword = sortedStars.map(star => star.spectralClass[0]).join("");

    function checkPassword() {
      // Get user input
      const userInput = document.getElementById("password").value.toUpperCase();
      
      // Check if the password is correct
      if (userInput === correctPassword) {
        document.getElementById("message").textContent = "Correct! Redirecting to the next task...";
        // Redirect to the next task after 2 seconds
        setTimeout(() => {
          window.location.href = "next_task.html"; // Replace with the actual next task URL
        }, 2000);
      } else {
        document.getElementById("message").textContent = "Incorrect password. Try again!";
      }
    }
  </script>
</body>
</html>
