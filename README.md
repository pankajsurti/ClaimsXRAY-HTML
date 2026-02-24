# ClaimsXRAY-HTML

This HTML sample helps sign in a user with Microsoft Entra ID and retrieve:
- ID Token
- Access Token

Follow the steps below before running the page.

## Prerequisites

1. Install [Visual Studio Code](https://code.visualstudio.com/).
2. Install the VS Code extension **Live Server**.
3. Make sure you have access to a Microsoft Entra application registration.

## Install Live Server extension (VS Code)

1. Open VS Code.
2. Select the **Extensions** icon from the left sidebar (or press `Ctrl+Shift+X`).
3. Search for `Live Server`.
4. Select extension **Live Server** by **Ritwick Dey**.
5. Click **Install**.
6. Reload VS Code if prompted.

## Step 1: Configure your Entra App Registration

1. Go to Microsoft Entra admin center.
2. Open **App registrations** and select your app.
3. Copy and keep these values:
	- **Application (client) ID**
	- **Directory (tenant) ID**

## Step 2: Update the HTML code

1. Open this project in VS Code.
2. Open `ClaimsXRay.html`.
3. Find the configuration section where tenant/client values are defined.
4. Replace placeholders/default values with your real values:
	- Application (client) ID
	- Tenant ID

## Step 3: Configure Live Server host

1. In VS Code, open **Settings**.
2. Search for **Live Server: Settings: Host**.
3. Change host value from `127.0.0.1` to `localhost`.

	You can also set it in `settings.json`:

	```json
	{
	  "liveServer.settings.host": "localhost"
	}
	```

## Step 4: Update Redirect URI in Entra

Because Live Server host is `localhost`, your redirect URI in Entra must also use `localhost`.

1. In your Entra app registration, open **Authentication**.
2. Under **Redirect URIs**, add/update the URI to match Live Server exactly (including port), for example:
	- `http://localhost:5500/ClaimsXRay.html`
3. Remove or stop using any redirect URI that points to `127.0.0.1` if your app now runs on `localhost`.
4. Save changes.

## Step 5: Run the HTML with Live Server

1. In VS Code, right-click `ClaimsXRay.html`.
2. Select **Open with Live Server**.
3. Complete sign-in.
4. Verify that ID Token and Access Token are returned on the page.

## Common issues

- **Redirect URI mismatch**: Ensure Entra redirect URI exactly matches protocol, host, port, and path used by Live Server.
- **Wrong tenant/client ID**: Recheck values in `ClaimsXRay.html`.
- **No token returned**: Confirm API permissions/consent are configured correctly in the Entra app.
