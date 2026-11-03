# Barbershop Booking System

A free booking page. Customers pick a service, date and time. Bookings are saved in a Google Sheet. The page is hosted on GitHub Pages.

```
Customer's phone  ->  GitHub Pages (index.html)  ->  Google Apps Script (Code.gs)  ->  Google Sheet
```

You need: a GitHub account and a Google account. Everything is free.

## Part 1: Set up the Google Sheet (the database)

1. Go to https://sheets.google.com and create a new blank spreadsheet. Name it "Barbershop Bookings".
2. Click **Extensions > Apps Script**.
3. Delete the code in the editor. Open `Code.gs` from this folder, copy everything and paste it in.
4. (Optional) Put your friend's email in `NOTIFY_EMAIL` at the top to get an email for each booking.
5. Click the **Save** icon.
6. Click **Deploy > New deployment**.
   - Click the gear icon and choose **Web app**.
   - Execute as: **Me**
   - Who has access: **Anyone**
   - Click **Deploy**, then **Authorize access** and allow permissions. (If Google warns "unverified app", click Advanced > Go to project. This is your own script.)
7. Copy the **Web app URL**. It looks like `https://script.google.com/macros/s/.../exec`.

## Part 2: Edit the booking page

Open `index.html` and change the `CONFIG` block near the bottom:

- `shopName`: the barbershop's name
- `apiUrl`: paste the Web app URL from Part 1
- `services`: the list of services
- `openTime` / `closeTime`: opening hours
- `slotMinutes`: length of each slot
- `closedWeekdays`: days off. `[1]` = closed Monday (0 = Sunday ... 6 = Saturday)

## Part 3: Put it on GitHub Pages

1. On https://github.com, click **New repository**. Name it e.g. `barbershop-booking`. Set it to **Public**. Create it.
2. Click **uploading an existing file**, drag in `index.html` (and this README), then **Commit changes**.
3. Go to **Settings > Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, Branch **main**, folder **/ (root)**. Save.
4. After 1-2 minutes your site is live at:
   `https://YOUR-USERNAME.github.io/barbershop-booking/`
5. Send that link to customers, put it in the Instagram bio or WhatsApp status, or make it a QR code for the shop door.

## Managing bookings

Open the Google Sheet. Each booking is a row. To cancel one, change **Status** from `Confirmed` to `Cancelled`. That time becomes free again on the page.

## If you change Code.gs later

Click **Deploy > Manage deployments > Edit (pencil) > Version: New version > Deploy**. The URL stays the same.

## Good to know

- Anyone with the link can book, so check the sheet daily.
- The page blocks double bookings, even if two people press Book at the same moment.
- It does not send SMS or WhatsApp reminders. You can add the email notification in step 4 of Part 1.
