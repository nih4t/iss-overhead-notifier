# ISS Overhead Notifier

This Python script sends an email notification when the International Space Station (ISS) is overhead and it's nighttime at your location.

## Features

- Tracks the current position of the ISS using the [Open Notify ISS API](http://open-notify.org/Open-Notify-API/ISS-Location-Now/).
- Checks if it's nighttime at your location using the [Sunrise-Sunset API](https://sunrise-sunset.org/api).
- Sends an email notification when the ISS is within a 5-degree range of your latitude and longitude, and it's night.

## How It Works

1. The script queries the ISS position using the ISS API.
2. It compares the ISS's position with your location to check if it's overhead (within a 5-degree range).
3. It queries the Sunrise-Sunset API to check if it's nighttime at your location.
4. If both conditions are met, it sends an email notification to the user.

## Installation

1. Clone this repository to your local machine.
    ```bash
    git clone https://github.com/yourusername/iss-overhead-notifier.git
    cd iss-overhead-notifier
    ```

2. Install the required Python packages:
    ```bash
    pip install requests
    ```

3. Set up your email credentials:
   - Update the `SENDER_EMAIL`, `PASSWORD`, and `RECEIVER_EMAIL` in the script with your Gmail account details. Make sure to use your Gmail App password for `PASSWORD`.

4. Replace `MY_LAT` and `MY_LONG` with your actual latitude and longitude.

## Usage

1. Run the script:
    ```bash
    python main.py
    ```

2. The script runs in an infinite loop, checking every 60 seconds whether the ISS is overhead and whether it is nighttime. If both conditions are true, an email notification will be sent to your specified receiver email.

## Environment Variables (Optional)

If you prefer not to hardcode your email and location information in the script, you can use environment variables. For example:

```bash
export SENDER_EMAIL="your-email@example.com"
export PASSWORD="your-app-password"
export RECEIVER_EMAIL="receiver-email@example.com"
export MY_LAT="your-latitude"
export MY_LONG="your-longitude"
```

Then modify the script to access these variables:
```python
import os

SENDER_EMAIL = os.getenv("SENDER_EMAIL")
PASSWORD = os.getenv("PASSWORD")
RECEIVER_EMAIL = os.getenv("RECEIVER_EMAIL")
MY_LAT = float(os.getenv("MY_LAT"))
MY_LONG = float(os.getenv("MY_LONG"))
```

## Requirements

- Python 3.x
- `requests` package
- Gmail account (with App password enabled for secure access)
