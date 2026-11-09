# Property Point Latur CRM

A private, mobile-friendly lead CRM for Property Point Latur. It's hosted free on GitHub Pages, with login and data stored in Supabase.

**What's in this folder**

| File | What it is |
|---|---|
| `index.html` | The CRM app |
| `config.js` | Your Supabase connection settings (you fill this in) |
| `supabase-setup.sql` | Creates the database tables and access rules (run once) |
| `README.md` | These steps |

Setup takes about 20 minutes. No coding is needed.

---

## Step 1: Create the Supabase project

1. Go to <https://supabase.com> and sign up with your Google or GitHub account.
2. Click **New project**.
   - **Name:** `property-point-crm`
   - **Database password:** create a strong one and save it somewhere safe.
   - **Region:** **South Asia (Mumbai)**, which is fastest for Latur.
3. Wait about 2 minutes while it sets up.

## Step 2: Create the database

1. In Supabase, open **SQL Editor** (left menu) and click **New query**.
2. Open `supabase-setup.sql`, copy everything, paste it into the editor and click **Run**.
3. You should see **"Success. No rows returned."**

## Step 3: Put the app on GitHub

1. Go to <https://github.com/new>.
   - **Repository name:** `crm` (or anything you like)
   - Set it to **Public**. GitHub Pages is free only for public repositories. Your leads are **not** in this repository; they live in Supabase behind login.
   - Click **Create repository**.
2. Click **uploading an existing file**. Drag in `index.html`, `config.js` and `README.md`, then click **Commit changes**.
   - Don't upload `supabase-setup.sql`. Keeping it out of the public repository is tidier.
3. Go to **Settings → Pages**. Under **Branch**, choose **main** and **/ (root)**, then click **Save**.
4. After a minute, your site address appears at the top of that page, for example `https://yourname.github.io/crm/`.

## Step 4: Connect the app to Supabase

1. In Supabase, open **Project Settings → API** (on newer screens, **API Keys**). Copy:
   - the **Project URL**
   - the **anon / public** key (on newer screens, the **publishable** key)
2. On GitHub, open `config.js`, click the ✏️ pencil icon, paste both values in place of the `YOUR-…` placeholders, and click **Commit changes**.

> ⚠️ Only use the **anon/publishable** key. It's designed to be public, and the database rules protect your data. **Never** put the `service_role` or `secret` key in any file on GitHub.

3. In Supabase, open **Authentication → URL Configuration**:
   - **Site URL:** your GitHub Pages address, for example `https://yourname.github.io/crm/`
   - **Redirect URLs:** add the same address.
   - Click **Save**. This makes email confirmation and password-reset links open your CRM.

## Step 5: Create your admin account

1. Open your site and click **Create an account**. Enter your name, email and a password.
2. Open the confirmation email from Supabase and click the link, then sign in.
3. **The first account created becomes the admin automatically.** Create yours before anyone else does.

## Step 6: Add your team

1. Ask Mahadev and Prathmesh to open the site and click **Create an account**.
2. They'll see **"Waiting for approval"**.
3. Sign in, go to **Team**, and click **Approve** for each person.

Anyone who finds the site can create an account, but they see **nothing** until you approve them. Approve only people you recognise.

---

## How access works

- **Admins** see all leads, assign and reassign leads, approve people, change roles and remove access.
- **Agents** add leads and see or edit **only the leads assigned to them**.
- The database enforces these rules, not just the screen, so they hold even if someone edits the page code.
- The duplicate check covers the whole team. An agent is told the number already exists and which agent has it, but can't open someone else's lead.
- The CRM always keeps at least one active admin.

## Good to know

- **Free-plan pause:** Supabase pauses free projects after about a week with no activity. Daily use keeps it awake. If it does pause, open the Supabase dashboard and click **Restore**.
- **Email limits:** Supabase's built-in email sender allows only a few emails per hour, which is fine for a small team. If sign-up emails stop arriving, wait an hour or add your own email service under **Authentication → Emails → SMTP Settings**.
- **Backups:** the free plan has no automatic point-in-time backups. To keep a copy, open **Table Editor → leads** and choose **Export to CSV** now and then.
- **Updating the app:** to change the app later, upload a new `index.html` to the repository. Your data in Supabase isn't affected.
- **Demo:** before `config.js` is filled in, the site shows a **"Connect your database"** screen with a button to open a demo that uses fictional leads.
