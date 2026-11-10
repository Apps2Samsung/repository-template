# Your own Apps2Samsung repository

Made a Tizen app and want people to install it with [Apps2Samsung](https://apps2samsung.com/)?
This template gives you your own **repository**: a list of your apps that people add once in
Apps2Samsung, and on the TV in [TV-Store](https://github.com/Apps2Samsung/TV-Store). From then on they
see your apps, with your name on them, and get every update you release.

No terminal, no code: everything below is clicking on GitHub. Setting it up takes about five minutes.

> **Only one app, and TV-Store doesn't matter to you?** Then you don't need this. People can add your
> app's GitHub link directly in Apps2Samsung, under **Settings > Installing > Your sources**. A
> repository adds TV-Store, several apps under one name, and a key that shows it's really you.

## Before you start

Your app needs to be on GitHub, in a **public** repository, with a **release** that has your `.wgt`
or `.tpk` file attached. Not done yet? See [Make a release of your app](#make-a-release-of-your-app)
below; it takes two minutes.

## Set it up

### 1. Make your copy

Click the green **Use this template** button at the top of this page, then **Create a new repository**.
Give it a name, for example `my-tizen-apps`, keep it **Public**, and click **Create repository**.

Everything from here on happens in *your* new repository, not in this one.

### 2. Turn on Pages

In your new repository: **Settings** (top right) > **Pages** (left). Under *Build and deployment*,
set **Source** to **GitHub Actions**. That's all: there is nothing to save.

### 3. Make your key

Open **[apps2samsung.com/repository-key](https://apps2samsung.com/repository-key/)**, type the name of
your repository and click **Make my key**. The page walks you through three steps: save a backup,
paste the key into your repository as a secret, and publish.

The key is made in your browser and never sent anywhere. Keep the backup safe: with the key, anyone
could publish apps in your name.

### 4. Add your app

In your repository: **Actions** (top) > **Add an app** (left) > **Run workflow** (right). Paste the
link to your app's GitHub repository, pick a category, and click the green **Run workflow** button.

After about a minute, **Actions > Publish** turns green. Click it: the summary shows your
repository's address. That's the one you give people.

```
https://<your-github-name>.github.io/<your-repository>/repository.json.signed
```

Your repository also gets its own page, `https://<your-github-name>.github.io/<your-repository>/`,
with the address, your key fingerprint and your apps. You can link to it from your app's README.

## Every day after that

- **You release a new version of your app:** nothing to do. Your repository picks it up within a day
  (or right away: Actions > Publish > Run workflow).
- **Another app:** Actions > Add an app, again.
- **Change a category or name:** Actions > Add an app with the same link and the new category or name.
- **Remove an app:** Actions > Remove an app.

## Something went wrong?

Open the red run in **Actions** and look at its **summary**: it says what's missing and links to the
right place. The usual ones: Pages isn't set to GitHub Actions, the key was pasted only partly (copy
it again from the key page), or the app has no release with a `.wgt` or `.tpk` file.

Still stuck? Ask in [Discussions](https://github.com/Apps2Samsung/tizen-community-packages/discussions).

## Make a release of your app

1. Open your **app's** repository on GitHub and click **Releases** (right side) > **Create a new release**
   (or go to `https://github.com/<your-github-name>/<your-app>/releases/new`).
2. **Choose a tag**: type a version, for example `v1.0.0`, and click **Create new tag**.
3. Give it a title, for example `1.0.0`.
4. Drag your `.wgt` or `.tpk` file into the box at the bottom (*Attach binaries*).
5. Click **Publish release**.

For each new version, make a new release the same way with a higher version number.

## Good to know

- **Your list is signed again every day**, even when nothing changed: Apps2Samsung stops trusting a
  list older than 7 days. GitHub can switch off daily runs in a quiet repository; this one switches
  itself back on.
- **People see that the apps come from you, not that Apps2Samsung checked them.** You are
  responsible for having the right to distribute what you publish.
- **Lost your key?** Make a new one on the key page and replace the secret. Everyone who added your
  repository then has to approve the new key, so keep the backup safe.
- **Your repository's id** is set when you add your first app, from your GitHub name and repository
  name. It never changes after that, even if you rename the repository.

## For the technically minded

The list lives in [`repository.input.json`](repository.input.json) once you've added an app; you can
also edit it by hand (each edit publishes). Every field is described in the
[template documentation](https://github.com/Apps2Samsung/tizen-community-packages/tree/main/templates/independent-repo)
and the format in
[docs/repositories.md](https://github.com/Apps2Samsung/tizen-community-packages/blob/main/docs/repositories.md).
A finished example: [Apps2Samsung/repository-example](https://github.com/Apps2Samsung/repository-example).

The workflows run the tools from
[tizen-community-packages](https://github.com/Apps2Samsung/tizen-community-packages) at `main`, so
fixes reach you automatically. To review every change yourself, pin `ref:` in the workflows to a
commit SHA.
