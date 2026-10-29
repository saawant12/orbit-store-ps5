# Notifications on your PS5, phone and computer

Orbit Store 1.7.5 can send PS5 notifications and optional notifications through [ntfy](https://ntfy.sh). In the default layout, open **App settings → Notifications**. Other layouts use **Settings → Notifications** in the browser and native app.

## Choose your alerts

Choose **On this PS5**, ntfy, or both. You can select download completion or failure, successful or failed package installation, and available Orbit updates. Installation notifications also say whether the downloaded package was deleted.

The service checks for a new release ten minutes after starting, then every six hours. It notifies you once per release; it does not install updates automatically.

## Set up ntfy

1. Open **Set up ntfy** or **Change ntfy settings**.
2. Enter your ntfy server address and topic. Use ntfy.sh or a server you operate.
3. Add a username and password if your server needs them. To use an access token, leave the username empty and enter the token in the password field.
4. Save, subscribe to the same topic in your phone or computer’s ntfy app, then choose **Send test notification**.

The saved password is not displayed again. Use a private, hard-to-guess topic or an authenticated server; anyone with access to an unprotected topic can read its notifications. The PS5 needs network access to the ntfy server. These alerts come from the Orbit service running on the PS5; they do not turn on phone access to Orbit’s control interface.

If a test fails, check the server address, topic, authentication and PS5 network access. PS5-only notifications can remain enabled independently.
