# MO API Client for Order Placement

## Overview

This client is designed to connect to the Motilal Oswal Open API for placing trading orders. It utilizes the official PythonSDK provided by Motilal Oswal to interact with the API services. The primary purpose of this client is to demonstrate the process of API client initialization, user login, and order placement.

## Prerequisites

Before you can use this client, ensure you have the following:

*   **Python 3.x**: Download and install from [python.org](https://www.python.org/).
*   **pip**: Python package installer, usually comes with Python 3.x.
*   **Motilal Oswal Trading Account & API Credentials**:
    *   `ApiKey`: Your unique API key.
    *   `UserID`: Your trading account user ID.
    *   `Password`: Your trading account password.
    *   `TwoFA`: Your second-factor authentication value (e.g., PAN, Date of Birth in YYYYMMDD format).
    *   `ClientCode`: Your client code (this might be the same as UserID for individual accounts; primarily used for dealer setups). This is used for API object initialization context.

## Setup

1.  **Clone or Download the Client**:
    If this client is part of a Git repository, clone it:
    ```bash
    git clone <repository_url>
    cd <repository_directory>/mo_api_client
    ```
    If you downloaded it as a ZIP, extract it and navigate to the `mo_api_client` directory.

2.  **Install Dependencies**:
    This client relies on packages listed in `requirements.txt` (which should be the one from the official PythonSDK). Install them using pip:
    ```bash
    pip install -r requirements.txt
    ```

## Configuration

You need to update the placeholder credentials in the `client.py` script with your actual Motilal Oswal API credentials and configuration.

Open `mo_api_client/client.py` and modify the following global variables:

*   `api_key`: Your Motilal Oswal API Key.
*   `userid`: Your Motilal Oswal User ID.
*   `password`: Your Motilal Oswal Password.
*   `two_fa`: Your Two-Factor Authentication value.
*   `client_code`: Your client code. For individual non-dealer accounts, this can often be `None` or the same as `userid`. It's used for the `MofslOpenApi` object's context.
*   `base_url`: The API base URL.
    *   UAT (Testing): `"https://openapi.motilaloswaluat.com"`
    *   Production (Live): `"https://openapi.motilaloswal.com"` (Ensure you are authorized for production access).
*   `source_id`: An identifier for your application (e.g., "MY_TRADING_APP").
*   `browser_name`: Can be "UNKNOWN" if not a browser-based client.
*   `browser_version`: Can be "UNKNOWN" if not a browser-based client.

**Example:**
```python
api_key = "YOUR_ACTUAL_API_KEY"
userid = "YOUR_ACTUAL_USER_ID"
password = "YOUR_ACTUAL_PASSWORD"
two_fa = "YOUR_ACTUAL_2FA_VALUE" # e.g., "19901231" for DOB or your PAN
client_code = "YOUR_ACTUAL_CLIENT_CODE" # or None
base_url = "https://openapi.motilaloswaluat.com" # For UAT
source_id = "MyPythonClient"
browser_name = "MyClient"
browser_version = "1.0"
```

**Security Recommendation**: For production environments, avoid hardcoding credentials directly in the script. Consider using environment variables, a secure configuration file, or a secrets management service.

## Usage

To run the client:

1.  Ensure you have configured your credentials in `client.py`.
2.  Navigate to the `mo_api_client` directory in your terminal.
3.  Execute the script:
    ```bash
    python client.py
    ```

The script will:
1.  Initialize the `MofslOpenApi` client.
2.  Attempt to log in to the API using the configured credentials.
3.  If login is successful, it will proceed to place a sample order.
4.  Print responses from the API at each step (initialization, login, order placement).

You can modify the `sample_order_details` dictionary within the `if __name__ == "__main__":` block in `client.py` to test different order types, instruments, quantities, or prices. Ensure the `symbol_token` corresponds to a valid instrument for the specified `exchange`.

## Disclaimer

This is a sample API client provided for demonstration and educational purposes. It should be tested thoroughly in a UAT (testing) environment before being considered for use with a live trading account.

**You are solely responsible for all actions, including any trades placed, orders submitted, or other API interactions made using this client or any modified version of it. The developers or providers of this sample client assume no liability for any financial losses, damages, or other consequences resulting from its use.** Always exercise caution and ensure you understand the risks involved in automated trading and API interactions.
