# Installing the Burp CA Certificate

## Step 1 — Download the certificate
- Make sure Burp Suite is running and your browser proxy is set to `127.0.0.1:8080`
- In your browser, go to: `http://burpsuite` or `http://127.0.0.1:8080`
- Click **CA Certificate** to download `cacert.der`

## Step 2 — Install in Firefox
1. Open **Settings** → search for **Certificates** → click **View Certificates**
2. Go to the **Authorities** tab → click **Import**
3. Select the downloaded `cacert.der` file
4. Check **Trust this CA to identify websites** → click **OK**
5. Restart Firefox

## Step 3 — Install in Chrome / Edge
1. Open **Settings** → search for **certificates** → click **Manage certificates**
2. Go to the **Trusted Root Certification Authorities** tab → click **Import**
3. Follow the wizard and select `cacert.der`
4. Click **Finish** and restart the browser

## Step 4 — Verify
- Visit any `https://` site with Burp intercept on
- You should see the request captured in Burp with no certificate warning in the browser
