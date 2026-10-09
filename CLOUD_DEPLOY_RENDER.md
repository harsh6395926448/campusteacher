# CampusSlot cloud deployment (Render)

This project is configured for Render with PostgreSQL. You must deploy it through your own GitHub/Render accounts; do not share account passwords or Gmail App Passwords in chat.

## Deploy
1. Extract this ZIP to a folder.
2. Create a private GitHub repository and upload the project files (do not upload `.env`, passwords, or database files).
3. In Render, choose **New + → Blueprint**, connect that repository, and deploy the `render.yaml` blueprint. It creates a web service and PostgreSQL database.
4. Once the service has a public URL like `https://campusslot-xxxx.onrender.com`, open Render → the `campusslot` web service → Environment. Set `BASE_URL` to that exact HTTPS URL, with no trailing slash, then save and redeploy.
5. Configure SMTP in the same Environment page: `SMTP_USERNAME` = your Gmail address; `SMTP_PASSWORD` = a Google App Password (not your regular Gmail password); `MAIL_FROM` = `CampusSlot <yourgmail@gmail.com>`. Keep these values private. A Google App Password generally requires 2-Step Verification on the Google account.
6. Open the public URL on laptop and phone. Test login and a fresh appointment email; test Login, View Appointment, Meeting Update, and teacher action links from mobile Gmail.

## Important notes
- The app's `BASE_URL` must be the public HTTPS address. Links containing `127.0.0.1` or `localhost` only point to the device opening the email, which is why they fail on phones.
- This deployment creates a new PostgreSQL database; it does not automatically copy records from the laptop's SQLite database. Migrate existing appointments/accounts before using it for real users.
- Check the current Render plan, database retention/expiry, and costs before relying on a free database for production.
- Never commit `.env`, SMTP credentials, secret keys, or real user data to GitHub.
- Deployment does not by itself guarantee mobile behavior; test the actual links on a phone after deployment.
