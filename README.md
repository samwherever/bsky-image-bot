# bsky-image-bot

This is a simple bot that posts an image to Bluesky on a cron job using GitHub Actions.

## How to use

1. Fork this repo
1. Put your images under `imagequeue/`. Only JPG and PNG images are supported by Bluesky. Commit and push.
1. Edit index.ts to customize parsing of your filenames into post text. Commit and push.
1. Generate an [app password](https://bsky.app/settings/app-passwords) for your Bluesky account.
1. Set Repository Secrets (`github.com/YOUR/REPO/settings/secrets/actions`) `BSKY_IDENTIFIER` and `BSKY_PASSWORD`. The `BSKY_IDENTIFIER` is your username, but _without_ the @ character, e.g. @YourName.bsky.social. If you configured an app password in step 4, use _that_ password for the `BSKY_PASSWORD` and _not_ the password you use to log in.
1. Create a [fine-grained GitHub personal token](https://github.com/settings/tokens?type=beta). Give it read/write access to repository variables.
1. Add the token as a secret named `REPO_ACCESS_TOKEN`.
1. Execute the `post-next-image` action from the GitHub UI.
1. When successful, edit `post-next-image.yml` to enable the automated post.
