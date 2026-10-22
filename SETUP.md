# Sutton Dinner Plan: setup guide

The dinner plan runs from GitHub Pages at **https://robbmx07.github.io/family-meal/**, with the plan saved in a Google Sheet. Erica and Mel never need an account. It works like the bill book: same kind of sheet, same family passcode.

You need about 10 minutes on a computer, plus **Code.gs**, the script Claude sent you. The passcode is already in it.

---

## Part 1: The repo

1. On GitHub, open the **Family-Meal** repo → **Settings**.
2. Rename it **family-meal** (all lowercase) and click **Rename**. Phones handle the lowercase address more reliably, the same fix you made for sutton-hp.
3. In **Settings → Pages**, under **Build and deployment**, set **Source** to **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.

## Part 2: The Google Sheet and script

1. Go to **sheets.new** while signed in to your Google account.
2. Rename the spreadsheet **Sutton Dinner Plan**. Use a new sheet, not the House Points or Bill Book one.
3. Open **Extensions → Apps Script**.
4. Delete the sample code, paste in all of **Code.gs**, and click **Save**.
5. In the function dropdown, choose **setup**, then click **Run**.
   1. Click **Review permissions** and choose your account.
   2. At "Google hasn't verified this app," click **Advanced**, then **Go to … (unsafe)**, then **Allow**. It asks for email permission so it can warn you if someone keeps guessing the passcode.
6. Click **Deploy → New deployment**, then the gear icon, then **Web app**.
   - **Execute as:** Me
   - **Who has access:** Anyone. The passcode is what protects it.
7. Click **Deploy**, then copy the **Web app URL**. It ends in `/exec`.

## Part 3: Connect the app to the sheet

Send the Web app URL to Claude, and Claude will put it in the app for you.

Or do it yourself:
1. On GitHub, open **family-meal → index.html** and click the pencil icon.
2. Search for `PASTE_YOUR_WEB_APP_URL_HERE` and replace it with your URL. Keep the quotes.
3. Click **Commit changes**. The site updates in a minute or two.

## Part 4: Everyone's phone

1. Text Erica and Mel the link: **https://robbmx07.github.io/family-meal/**
2. Tell them the passcode in person or on a call, not in the same text.
3. Each person opens the link in **Safari**, enters the passcode, taps **Unlock**, then **Share → Add to Home Screen**.

---

## Good to know

- **Syncing.** Each phone checks for changes every 20 seconds while the app is open, and whenever you switch back to it. Changes made with no signal save once the phone reconnects. The top line says "Saving…" until they do.
- **Wrong passcodes.** After 10 wrong tries, the dinner plan locks for 6 hours and you get an email.
- **Changing the passcode.** In Apps Script, edit the `FAMILY_PASSCODE` line and save. Then **Deploy → Manage deployments**, the pencil icon, set **Version** to **New version**, and click **Deploy**. The URL stays the same, and each phone asks for the new passcode.
- **Readable copy in the sheet.** In the Google Sheet, use **Dinner Plan → Refresh readable tab** for plain **Plan** and **Prep** tabs. Don't edit the `store` tab by hand; it's the app's raw data.
- **Lock.** The **Lock** button at the top makes that phone ask for the passcode again.
- **Privacy.** The app's code is public on GitHub, but the plan and the passcode aren't. They stay in your Google Sheet. Never upload Code.gs to GitHub.
