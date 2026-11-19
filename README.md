# My link page

A link-in-bio page that lives on GitHub Pages. You edit one text file, `profile.hjson`, and GitHub builds and publishes the page for you. No coding needed.

<!-- screenshot: the finished starter page -->

## Set it up

1. Click the green **Use this template** button at the top of this repository, then **Create a new repository**. Pick a name and make it **Public**.
   <!-- screenshot: the Use this template button -->
2. In your new repository, open **Settings**, then **Pages**.
3. Under **Build and deployment**, set **Source** to **GitHub Actions**.
   <!-- screenshot: Settings, Pages, Source set to GitHub Actions -->
4. Go back to the **Code** tab and click `profile.hjson`, then the pencil icon (Edit).
5. Change the values to your own name, bio and links. See the rules below.
   <!-- screenshot: editing profile.hjson on github.com -->
6. Click **Commit changes**.
7. Open the **Actions** tab. Wait for the yellow dot to turn into a green tick (about a minute). If you see a red cross from before you turned on Pages, ignore it: your commit in step 6 starts a new run. If no new run appears, open **Actions**, click the deploy workflow, and press **Run workflow**.
8. Your page is live. Its address is `https://<your-username>.github.io/<repository-name>/`. The full address is also shown in **Settings**, **Pages**. If your repository is named `<your-username>.github.io`, the page is at `https://<your-username>.github.io/` with no repository name.

Every time you commit a change to `profile.hjson`, the page updates the same way.

The full guide, with every field, theme and error message, is at https://olakunlevpn.github.io/linkprofile/docs/.

## The three rules for `profile.hjson`

The file is written in Hjson, a forgiving kind of JSON. Keep these three things in mind and you will rarely hit a problem.

1. **A value runs to the end of the line.** If you write `name: Ann # my name`, the name becomes `Ann # my name`. Put comments on their own line, starting with `#`.
2. **One-line objects need quotes.** If you put several fields on one line inside `{ }`, quote the values: `{ type: "github", url: "https://github.com/you" }`. Otherwise, put each field on its own line.
3. **Quote colours.** Write `color: "#34d399"`. Without quotes, the `#` starts a comment.

## Change the look

Set the theme near the top of `profile.hjson`:

```
theme: classic
```

To see the available themes, run `npx linkprofile themes` on your computer (needs Node 22 or newer), then put the name you like after `theme:`.

Five themes come built in: `classic` (the default), `bento`, `cover`, `crimson` and `editorial`.

### Light or dark

The `classic` theme follows each visitor's light or dark system setting, and shows a small switch in the top-right corner so they can change it. To always use one look, use the long form of `theme` and set `mode`:

```
theme: { name: "classic", options: { mode: "dark" } }
```

`mode` can be `auto` (the default), `light` or `dark`. The switch only appears in `auto` mode; to hide it there too, add `toggle: false`, like `options: { toggle: false }`. Keep the quotes: the values share one line.

The other themes take the same `mode` values (`auto`, `light` or `dark`). `cover` follows the system, and `bento`, `crimson` and `editorial` are dark by default. Every theme also takes an `accent` colour, for example `options: { accent: "#ff6b6b" }`. In `classic` and `bento` it colours the dot after your name (`bento` also tints the glow behind the page); in `cover` it colours the banner, in `crimson` the glow, the link icons and the links heading, and in `editorial` the background gradient.

## Change your picture

1. Open the `images` folder and choose **Add file**, then **Upload files**. Upload your picture as a **PNG or JPG**. Link previews on social sites often do not show SVG pictures.
2. Commit the upload.
3. In `profile.hjson`, set `avatar` to the new file, for example `avatar: images/me.jpg`.

You can also use a full `https://` address instead of a file.

The starter also uses `images/avatar.png` as the page icon in the browser tab (`meta.favicon`). Point that at your new file too, or the old picture stays there.

## If something goes wrong

If the page does not update, the build probably found a mistake in `profile.hjson`.

1. Open the **Actions** tab and click the latest run with a red cross.
2. Click the **build** job, then open the **Build** step.
3. The message says what is wrong, where, and how to fix it. Fix it in `profile.hjson` and commit again.

<!-- screenshot: a failed run with the error message in the Build step -->

## Optional: preview on your computer

If you have Node 22 or newer, you can see changes before you publish them. Download your repository with **Code**, then **Download ZIP** (or use `git clone`), unzip it, open a terminal in that folder, and run:

```
npx linkprofile preview
```

Open the address it prints (`Preview at http://127.0.0.1:...`). The page reloads when you save `profile.hjson`.

## Optional: use your own domain

1. In **Settings**, **Pages**, enter your domain under **Custom domain**, for example `links.example.com`, and click **Save**.
2. Set up the DNS records your domain provider needs (GitHub's Pages documentation lists them). When the domain check succeeds, tick **Enforce HTTPS**.
3. Commit any change, or re-run the workflow from **Actions**. The page is rebuilt with your domain as its address.

Step-by-step instructions, with the DNS records: https://olakunlevpn.github.io/linkprofile/docs/custom-domain/

## Optional: add other files

Everything in the `public` folder is copied to your site as it is, for example a `robots.txt`.
