<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SCP Foundation Secure Login</title>
    <style>
        /* Basic Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Körper Styling */
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: #fff;
            font-family: 'Courier New', Courier, monospace;
            overflow: hidden;
            position: relative;
            background-color: #000;
        }

        /* Gruseliger Hacker Hintergrund */
        @keyframes rain {
            0% { transform: translateY(-100vh); opacity: 1; }
            100% { transform: translateY(100vh); opacity: 0; }
        }

        .hacker-background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .hacker-background .char {
            position: absolute;
            top: -100px;
            color: #00ff00;
            font-size: 20px;
            font-family: 'Courier New', Courier, monospace;
            opacity: 0.7;
            animation: rain 4s linear infinite;
            white-space: nowrap;
        }

        /* Animation für zufällige Bewegungen */
        .hacker-background .char:nth-child(odd) {
            animation-duration: 5s;
            animation-delay: -1s;
        }

        .hacker-background .char:nth-child(even) {
            animation-duration: 6s;
            animation-delay: -2s;
        }

        /* Login Box Styling */
        .login-box {
            background: rgba(20, 20, 20, 0.85);
            padding: 2rem;
            border-radius: 12px;
            box-shadow: 0 0 20px rgba(255, 0, 0, 0.5), 0 0 30px rgba(0, 0, 255, 0.5);
            text-align: center;
            max-width: 350px;
            width: 100%;
            z-index: 1;
            position: relative;
        }

        /* SCP Logo */
        .scp-logo {
            font-size: 3rem;
            color: #FF0000;
            text-shadow: 0 0 5px #FF0000, 0 0 10px #FF0000;
            letter-spacing: 2px;
            animation: glitch 1.5s infinite alternate;
        }

        /* SCP Logo Glitch Animation */
        @keyframes glitch {
            0% { transform: translate(0); }
            20% { transform: translate(-1px, 1px); }
            40% { transform: translate(1px, -1px); }
            60% { transform: translate(-1px, -1px); }
            80% { transform: translate(1px, 1px); }
            100% { transform: translate(0); }
        }

        /* Eingabefelder */
        .login-box input[type="text"],
        .login-box input[type="password"] {
            width: 100%;
            padding: 0.8rem;
            margin: 0.5rem 0;
            border: none;
            border-radius: 8px;
            background-color: #222;
            color: #ddd;
            font-size: 1rem;
            outline: none;
        }

        /* Fehlermeldung */
        .error-message {
            color: #ff4d4d;
            font-size: 0.9rem;
            margin-top: 1rem;
            display: none;
        }

        /* Login Button */
        .login-button {
            padding: 0.8rem;
            width: 100%;
            border: none;
            border-radius: 8px;
            background: linear-gradient(45deg, #ff0000, #8b0000);
            color: #fff;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 1rem;
        }

        .login-button:hover {
            background: linear-gradient(45deg, #8b0000, #ff0000);
            box-shadow: 0 0 10px rgba(255, 0, 0, 0.6);
        }

        /* Footer */
        .scp-footer {
            margin-top: 2rem;
            font-size: 0.8rem;
            color: #555;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
    </style>
</head>
<body>
    <!-- Hacker Hintergrund mit fallenden Zeichen -->
    <div class="hacker-background">
        <!-- Hier fügen wir dynamisch die fallenden Zeichen hinzu -->
    </div>

    <!-- Login Box -->
    <div class="login-box">
        <div class="scp-logo">SCP Foundation</div>
        <h1>Secure Login</h1>
        
        <form onsubmit="displayError(event)">
            <input type="text" placeholder="Benutzername" required>
            <input type="password" placeholder="Passwort" required>
            <button type="submit" class="login-button">Einloggen</button>
            <div class="error-message" id="error-message">Falsches Passwort oder falscher Benutzername</div>
        </form>
        
        <div class="scp-footer">
            Zugriff nur für autorisiertes Personal. Unbefugter Zugriff wird geahndet.
        </div>
    </div>

    <script>
        // Dynamisch zufällige Zeichen in den Hintergrund einfügen
        function createHackerEffect() {
            const hackerBackground = document.querySelector('.hacker-background');
            const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
            
            // Zufällige Zeichen generieren und auf den Bildschirm bringen
            for (let i = 0; i < 200; i++) {
                const char = document.createElement('span');
                char.className = 'char';
                char.innerText = characters.charAt(Math.floor(Math.random() * characters.length));
                char.style.left = `${Math.random() * 100}vw`;
                char.style.animationDelay = `${Math.random() * 5}s`;
                hackerBackground.appendChild(char);
            }
        }

        // Fehleranzeige nach Login versuchen
        function displayError(event) {
            event.preventDefault(); // Verhindert das Absenden des Formulars
            document.getElementById('error-message').style.display = 'block'; // Zeigt die Fehlermeldung an
        }

        // Hacker-Effekt beim Laden der Seite aktivieren
        window.onload = createHackerEffect;
    </script>
</body>
</html>

