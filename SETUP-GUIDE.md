# Putting the Vipers site on nvvipers.com

This takes about an hour, one time. After that, you update the site at **nvvipers.com/admin**.

You'll set up three free things:

1. **GitHub** stores the website files.
2. **Netlify** shows the files to the world at nvvipers.com.
3. **GoDaddy** (where you bought the domain) gets told to send visitors to Netlify.

Websites change their menus from time to time. If a button below has a slightly different name, look for the closest match.

---

## Part 1: Put the files on GitHub (about 15 minutes)

1. Unzip **nvvipers-site.zip** on your computer. You'll get a folder called `nvvipers-site`.
2. Go to **github.com** and sign up for a free account. Write down your **username**; you'll need it in Part 4.
3. Click the **+** in the top-right corner, then **New repository**.
   - Repository name: `nvvipers-site`
   - Choose **Public** (the site is public anyway, and this keeps the editor simple).
   - Check **Add a README file**.
   - Click **Create repository**.
4. On the new repository page, click **Add file → Upload files**.
5. Open the `nvvipers-site` folder on your computer, select **everything inside it** (the `admin`, `content` and `images` folders plus `index.html`, `site.css`, `netlify.toml` and this guide), and drag it all onto the GitHub page.
   - Drag the *contents* of the folder, not the folder itself.
6. Wait for the files to finish uploading, then click **Commit changes**.
7. Check: you should now see `admin`, `content`, `images`, `index.html`, `netlify.toml` and `site.css` listed in the repository.

---

## Part 2: Put the site online with Netlify (about 10 minutes)

1. Go to **netlify.com** and choose **Sign up**, then **Sign up with GitHub**. Approve the connection.
2. Choose **Add new site** (or **Add new project**) → **Import an existing project** → **GitHub**.
3. Pick the `nvvipers-site` repository. If you don't see it, use the link to give Netlify access to it.
4. On the settings screen, leave **Build command** empty and set **Publish directory** to `.` (just a period). Click **Deploy**.
5. In a minute or so, Netlify shows a temporary web address like `something-random.netlify.app`. Open it. You should see the Vipers site with your schedule.
6. Optional: under **Site configuration → Change site name**, rename it to something like `nvvipers` so the temporary address is `nvvipers.netlify.app`.

---

## Part 3: Connect nvvipers.com through GoDaddy (about 15 minutes, then waiting)

### In Netlify
1. Open your site in Netlify and go to **Domain management** (sometimes **Domains**).
2. Click **Add a domain** (or **Add custom domain**), type `nvvipers.com`, and confirm you own it.
3. Netlify will ask you to set up DNS records. **Choose the option to use external DNS** (keep your DNS at GoDaddy). This avoids disturbing anything else on the domain, such as email.
4. Netlify shows the records to add. They are usually:
   - An **A** record for `@` pointing to `75.2.60.5`
   - A **CNAME** record for `www` pointing to your Netlify address (for example `nvvipers.netlify.app`)

   **Use whatever Netlify shows you** if it differs from the above.

### In GoDaddy
1. Sign in at **godaddy.com** → **My Products** → find nvvipers.com → **DNS** (or **Manage DNS**).
2. Look for an existing **A** record with the name `@`. **Edit it** so the value is Netlify's address (`75.2.60.5`). If there are other A records for `@`, delete them so only Netlify's remains.
3. Look for a **CNAME** record named `www`. **Edit it** to point to your Netlify address (for example `nvvipers.netlify.app`). If none exists, add one.
4. If GoDaddy has **Domain Forwarding** turned on for nvvipers.com, turn it off; it would override these records.
5. Save.

### Wait, then check
- Changes usually take effect within an hour, occasionally up to a day.
- Back in Netlify's **Domain management**, the domain will show as verified, and Netlify will turn on **HTTPS** (the padlock) automatically. If it offers a button to provision a certificate, click it.
- Visit **nvvipers.com**. You should see the site.

---

## Part 4: Turn on the editor at nvvipers.com/admin (about 15 minutes)

The editor logs in with your GitHub account. This part lets GitHub and Netlify trust each other.

### A. Tell the editor which repository to use
1. On GitHub, open your `nvvipers-site` repository → `admin` folder → `config.yml`.
2. Click the **pencil** (Edit) icon.
3. On the line `repo: YOUR-GITHUB-USERNAME/nvvipers-site`, replace `YOUR-GITHUB-USERNAME` with your actual GitHub username. Example: `repo: vipersmom/nvvipers-site`
4. Click **Commit changes**.

### B. Create a GitHub login app
1. On GitHub, click your profile picture → **Settings** → scroll to **Developer settings** (bottom of the left menu) → **OAuth Apps** → **New OAuth App**.
2. Fill in:
   - **Application name:** `Vipers site editor`
   - **Homepage URL:** `https://nvvipers.com`
   - **Authorization callback URL:** `https://api.netlify.com/auth/done`
3. Click **Register application**.
4. Copy the **Client ID**. Then click **Generate a new client secret** and copy the secret right away (GitHub only shows it once).

### C. Give those to Netlify
1. In Netlify, open your site → **Site configuration** → **Access & security** (or **Access control**) → **OAuth**.
2. Under **Authentication providers**, click **Install provider** → choose **GitHub**.
3. Paste the **Client ID** and **Client secret**. Save.

### D. Try it
1. Go to **nvvipers.com/admin** and click **Login with GitHub**. Approve the request.
2. You should see four sections: **Schedule**, **Announcement**, **Club info**, and **FAQ**.

---

## Using the editor

Everything is at **nvvipers.com/admin**. After you click **Publish**, the live site updates in about a minute. Refresh the page to see it.

**Add a game or tournament:** Schedule → Games and tournaments → **Add event** → choose **Game** or **Tournament** → fill in the fields → **Publish**.
- Times are typed like `9:00 AM` or `5:05 PM`.
- For a tournament whose games aren't out yet, turn on **Game schedule TBD**. When the schedule is released, turn it off and use **Add game** for each game (time, opponent, field, game type). Add scores afterward.
- You don't need to delete old events. Past events move into "Past events and results" by themselves.

**Post an announcement:** Announcement → turn on **Show announcement** → add a title, message, and (optionally) button text and link → **Publish**. To take it down, turn **Show announcement** off and publish. You can also set **Hide after** so it disappears on its own after a date. The banner appears above the Schedule.

**Change the photo:** Club info → **Photo** → choose a new image (upload from your computer) → **Publish**. Tall, portrait-style photos fit best. Update **Photo description** too.

**Update the FAQ:** FAQ → FAQ page → open a section → edit a question's answer, or use **Add question** / **Add section** → **Publish**. In an answer, start a line with `-` for a bullet. Add **Button text** and **Button link** to show a button (for example, a link to the player or coach interest form).

**Switch background:** Club info → **Background style** → Snake scales or Classic (plain).

**Let another coach or parent edit:** On GitHub, open the repository → **Settings** → **Collaborators** → **Add people** and enter their GitHub username. They can then log in at nvvipers.com/admin too.

---

## If something goes wrong

- **The site shows old info after publishing:** wait a minute and refresh. Netlify rebuilds after each publish.
- **"Login with GitHub" fails:** recheck Part 4. The callback URL must be exactly `https://api.netlify.com/auth/done`, and the `repo:` line in `config.yml` must match your username and repository name exactly.
- **nvvipers.com doesn't load after a day:** in GoDaddy DNS, confirm the `@` A record and `www` CNAME match what Netlify asked for, and that Domain Forwarding is off.
- **Something got deleted by mistake:** every change is saved in GitHub's history. Open the repository → click the **commits** count to see past versions.
