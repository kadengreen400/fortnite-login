# fortnite-login 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Fortnite Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: black;
            color: white;
            margin: 0;
            padding: 0;
        }

        /* Login Page Styles */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
        }

        h1 {
            color: red;
            font-size: 2.5em;
            margin-bottom: 20px;
        }

        .login-form {
            background-color: #222;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(255, 0, 0, 0.7);
            width: 300px;
            text-align: center;
        }

        .login-form input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            background-color: #333;
            border: 1px solid red;
            border-radius: 5px;
            color: white;
        }

        .login-form button {
            width: 100%;
            padding: 12px;
            background-color: red;
            border: none;
            border-radius: 5px;
            color: white;
            cursor: pointer;
        }

        .login-form button:hover {
            background-color: darkred;
        }

        .login-form p {
            color: white;
            font-size: 0.9em;
        }

        /* Main Page Styles */
        header {
            background-color: red;
            padding: 20px;
            text-align: center;
            font-size: 2em;
        }

        .container {
            padding: 20px;
        }

        h2 {
            color: red;
        }

        .section {
            margin-bottom: 40px;
        }

        .section img {
            max-width: 100%;
            border-radius: 8px;
        }

        .video {
            margin: 20px 0;
        }

        .video iframe {
            width: 100%;
            height: 400px;
            border: none;
        }

        .stats, .achievements, .skins {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
        }

        .stats div, .achievements div, .skins div {
            width: 30%;
            background-color: #222;
            padding: 10px;
            border-radius: 8px;
            text-align: center;
            margin: 10px 0;
        }

        .stats div h3, .achievements div h3, .skins div h3 {
            color: red;
        }

        footer {
            background-color: red;
            text-align: center;
            padding: 10px;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

    </style>
</head>
<body>

<!-- Login Page -->
<div class="login-container">
    <h1>Fortnite Login</h1>
    <div class="login-form">
        <form action="main-page.html" method="POST">
            <input type="text" id="username" name="username" placeholder="Username" required><br>
            <input type="password" id="password" name="password" placeholder="Password" required><br>
            <button type="submit">Login</button>
        </form>
        <p>Don't have an account? <a href="#" style="color: red;">Sign up</a></p>
    </div>
</div>

<!-- Main Content Page After Login -->
<header>
    <h1>Your Fortnite Page</h1>
</header>

<div class="container">
    <section class="section highlights">
        <h2>Highlights</h2>
        <p>Show off your best Fortnite moments!</p>
        <div class="video">
            <iframe src="https://www.youtube.com/embed/your-video-id" title="Fortnite Highlight Video"></iframe>
        </div>
    </section>

    <section class="section stats">
        <h2>Game Stats</h2>
        <div>
            <h3>Kills</h3>
            <p>1000</p>
        </div>
        <div>
            <h3>Wins</h3>
            <p>200</p>
        </div>
        <div>
            <h3>Top 10</h3>
            <p>500</p>
        </div>
        <div>
            <h3>Total Playtime</h3>
            <p>150 Hours</p>
        </div>
        <div>
            <h3>Win Rate</h3>
            <p>20%</p>
        </div>
        <div>
            <h3>Avg. Kills per Game</h3>
            <p>5</p>
        </div>
    </section>

    <section class="section achievements">
        <h2>Achievements</h2>
        <div>
            <h3>Victory Royale</h3>
            <p>Earned 50 times</p>
        </div>
        <div>
            <h3>High Kill Game</h3>
            <p>Max: 20 kills</p>
        </div>
    </section>

    <section class="section skins">
        <h2>Favorite Skins</h2>
        <div>
            <h3>Skin 1</h3>
            <img src="skin1-image.jpg" alt="Skin 1">
        </div>
        <div>
            <h3>Skin 2</h3>
            <img src="skin2-image.jpg" alt="Skin 2">
        </div>
    </section>
</div>

<footer>
    <p>Follow me on social media for more Fortnite content!</p>
</footer>

</body>
</html> 
async function getFortniteStats(accessToken) {
    const statsUrl = 'https://api.epicgames.com/fortnite/stats'; // Example API URL (verify with Epic Games API docs)

    try {
        const response = await axios.get(statsUrl, {
            headers: {
                Authorization: `Bearer ${accessToken}`,
            },
        });

        return response.data;
    } catch (error) {
        console.error('Error fetching Fortnite stats:', error);
        return null;
    }
} 
<a href="https://www.epicgames.com/id/login?client_id=YOUR_CLIENT_ID&redirect_uri=YOUR_REDIRECT_URI&response_type=code&scope=basic_profile">
    <button>Login with Epic Games</button>
</a>
const axios = require('axios');

// Endpoint to exchange authorization code for access token
const tokenUrl = 'https://api.epicgames.com/oauth/token';

// Your Epic Games Client ID and Secret
const clientId = 'YOUR_CLIENT_ID';
const clientSecret = 'YOUR_CLIENT_SECRET';

// Example function to handle the exchange
async function exchangeCodeForToken(authCode, redirectUri) {
    try {
        const response = await axios.post(tokenUrl, {
            code: authCode,
            client_id: clientId,
            client_secret: clientSecret,
            redirect_uri: redirectUri,
            grant_type: 'authorization_code'
        });
        return response.data.access_token;
    } catch (error) {
        console.error('Error exchanging code for token:', error);
        return null;
    }
}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Your Fortnite Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: black;
            color: white;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: red;
            padding: 20px;
            text-align: center;
            font-size: 2em;
        }

        .container {
            padding: 20px;
        }

        h2 {
            color: red;
        }

        .section {
            margin-bottom: 40px;
        }

        .section img {
            max-width: 100%;
            border-radius: 8px;
        }

        .video {
            margin: 20px 0;
        }

        .video iframe {
            width: 100%;
            height: 400px;
            border: none;
        }

        .stats, .achievements, .skins {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
        }

        .stats div, .achievements div, .skins div {
            width: 30%;
            background-color: #222;
            padding: 10px;
            border-radius: 8px;
            text-align: center;
            margin: 10px 0;
        }

        .stats div h3, .achievements div h3, .skins div h3 {
            color: red;
        }

        footer {
            background-color: red;
            text-align: center;
            padding: 10px;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>

<header>
    <h1>Your Fortnite Page</h1>
</header>

<div class="container">
    <section class="section highlights">
        <h2>Highlights</h2>
        <p>Show off your best Fortnite moments!</p>
        <div class="video">
            <iframe src="https://www.youtube.com/embed/your-video-id" title="Fortnite Highlight Video"></iframe>
        </div>
    </section>

    <section class="section stats">
        <h2>Game Stats</h2>
        <div>
            <h3>Kills</h3>
            <p>1000</p>
        </div>
        <div>
            <h3>Wins</h3>
            <p>200</p>
        </div>
        <div>
            <h3>Top 10</h3>
            <p>500</p>
        </div>
        <div>
            <h3>Total Playtime</h3>
            <p>150 Hours</p>
        </div>
        <div>
            <h3>Win Rate</h3>
            <p>20%</p>
        </div>
        <div>
            <h3>Avg. Kills per Game</h3>
            <p>5</p>
        </div>
    </section>

    <section class="section achievements">
        <h2>Achievements</h2>
        <div>
            <h3>Victory Royale</h3>
            <p>Earned 50 times</p>
        </div>
        <div>
            <h3>High Kill Game</h3>
            <p>Max: 20 kills</p>
        </div>
    </section>

    <section class="section skins">
        <h2>Favorite Skins</h2>
        <div>
            <h3>Skin 1</h3>
            <img src="skin1-image.jpg" alt="Skin 1">
        </div>
        <div>
            <h3>Skin 2</h3>
            <img src="skin2-image.jpg" alt="Skin 2">
        </div>
    </section>
</div>

<footer>
    <p>Follow me on social media for more Fortnite content!</p>
</footer>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Fortnite Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: black;
            color: white;
            margin: 0;
            padding: 0;
        }

        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
        }

        h1 {
            color: red;
            font-size: 2.5em;
            margin-bottom: 20px;
        }

        .login-form {
            background-color: #222;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(255, 0, 0, 0.7);
            width: 300px;
            text-align: center;
        }

        .login-form input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            background-color: #333;
            border: 1px solid red;
            border-radius: 5px;
            color: white;
        }

        .login-form button {
            width: 100%;
            padding: 12px;
            background-color: red;
            border: none;
            border-radius: 5px;
            color: white;
            cursor: pointer;
        }

        .login-form button:hover {
            background-color: darkred;
        }

        .login-form p {
            color: white;
            font-size: 0.9em;
        }
    </style>
</head>
<body>

<div class="login-container">
    <h1>Fortnite Login</h1>
    <div class="login-form">
        <form action="main-page.html" method="POST">
            <input type="text" id="username" name="username" placeholder="Username" required><br>
            <input type="password" id="password" name="password" placeholder="Password" required><br>
            <button type="submit">Login</button>
        </form>
        <p>Don't have an account? <a href="#" style="color: red;">Sign up</a></p>
    </div>
</div>

</body>
</html>
