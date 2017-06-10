## Secure Tokens

As part of Chai's standards, we use [Continuous Integration](https://en.wikipedia.org/wiki/Continuous_integration) and Continuous Deployment via [semantic-release](https://en.wikipedia.org/wiki/Continuous_integration). To enable these to happen, we need to provide our CI server - [Travis](https://travis-ci.org/) with the right environment variables to gain access to our Saucelabs accounts (for cross browser testing), Github account (for automatically posting release notes), and our NPM account (for publishing packages).

We cannot store these in plaintext, because that means anyone who had them could publish whatever they wanted through the chaijs user - for example overwriting the `chai` npm package with a virus. As such, we encrypt these tokens in the codebase.

### Who can access the real tokens?

The users in the [token-bearers](https://github.com/orgs/chaijs/teams/token-bearers) team can view, create and revoke secure repository tokens. If you need a token created or regenerated for your repository, you should @mention the token-bearers team, so they may generate some tokens for your repository.

### How are the tokens generated?

As of writing this, we generate unique tokens for each new repository, for each of the accounts we have, and encrypt these values into the `.travis.yml` file. The process is as follows:

#### Generating a Saucelabs token

1. In a new Incognito Browsing window, visit https://saucelabs.com/beta/team-management, and enter the saucelabs username and password you have. You'll also need to follow any 2FA prompts.
2. Scroll to the bottom of the page, where you should see the saucelabs team users - one for each repository
3. Add the new repository - by clicking add user.
4. Make the `First Name` `Chaijs`, `Last Name` the name of the repo. The email should be `chaijs+{repo}@keithcirkel.co.uk` (where `{repo}` is the name of the repo). Make the password the same as the parent account.
5. With the user generated, click into the user account, click "Edit User Info", and here you should see an "Access Key" section. Click "Show" and copy the token.
6. Prepend `SAUCE_ACCESS_KEY=` to the token, you should have something like `SAUCE_ACCESS_KEY=d9167f44-edfc-4eb3-b0d3-310b7e75cb40` on your clipboard.
5. In the repository folder (on a Mac), run `pbpaste | travis encrypt -r chaijs/{repo}` (where `{repo}` is the repo name)
6. This will output something like the following:
   ```
   Please add the following to your .travis.yml file:
   secure: "QEQUy9IvdWbxcMTub3VvH4Ru2sCI3Ze/bWJ2pammucjQ1u1hqfeJf3NAFOlfrbpx52xlIiqgBwm6u2sDRZ69sLYkak/je5GCtE9rLhxoqiS1l6GlRZ9qnBrW7e790ja4aJdjeazULE3F6kgJwcy8E3qLA5eQOt9kdzevSU50AIQ="
   Pro Tip: You can add it automatically by running with --add.
   ```
7. (Pro Pro Tip: Dont use `--add` because it reformats the `.travis.yml` and strips comments. No fun.)
8. Copy the `secure:` bit, and add it to the array of `env.global` in the `.travis.yml`. Make sure to add a comment mentioning that this is the SAUCE_ACCESS_KEY.
9. You also need to add `SAUCE_USERNAME=chaijs-{repo}` (where `{repo}` is the name of the repository). This doesn't need to be encrypted, so you can add it in plaintext to the `.travis.yml`.
10. Submit a PR to the respective repository.


#### Generating an NPM token

1. On the command line, run `npm login --userconfig /tmp/chai-delete-me` and follow the prompts; the username is `chaijs`, the password you should have, and the email is `chaijs@keithcirkel.co.uk`.
2. This generates a token and puts it in the `/tmp/chai-delete-me` file
3. Run `cat /tmp/chai-delete-me` to expose the token. You should see something like:
   ```
   //registry.npmjs.org/:_authToken=d9167f44-edfc-4eb3-b0d3-310b7e75cb40
   ```
4. Copy the UUID part, and prepend `NPM_TOKEN=` to this. You should end up with something like `NPM_TOKEN=d9167f44-edfc-4eb3-b0d3-310b7e75cb40` on your clipboard.
5. In the repository folder (on a Mac), run `pbpaste | travis encrypt -r chaijs/{repo}` (where `{repo}` is the repo name)
6. This will output something like the following:
   ```
   Please add the following to your .travis.yml file:
   secure: "QEQUy9IvdWbxcMTub3VvH4Ru2sCI3Ze/bWJ2pammucjQ1u1hqfeJf3NAFOlfrbpx52xlIiqgBwm6u2sDRZ69sLYkak/je5GCtE9rLhxoqiS1l6GlRZ9qnBrW7e790ja4aJdjeazULE3F6kgJwcy8E3qLA5eQOt9kdzevSU50AIQ="
   Pro Tip: You can add it automatically by running with --add.
   ```
7. (Pro Pro Tip: Dont use `--add` because it reformats the `.travis.yml` and strips comments. No fun.)
8. Copy the `secure:` bit, and add it to the array of `env.global` in the `.travis.yml`. Make sure to add a comment mentioning that this is the NPM_TOKEN, and copy the last section of the token - so that we can revoke it if we need to.
9. **DELETE `/tmp/chai-delete-me`**. On the command line this is `rm -f /tmp/chai-delete-me`.
10. Submit a PR to the respective repository.

#### Generating a GitHub token

1. In a new Incognito Browsing window, visit https://github.com/login, and enter the `chaijs-bot` username and password you have. You'll also need to follow the 2FA prompts. You should have a 2FA token for this user.
2. Go to https://github.com/settings/tokens/new
3. Generate a new token, calling it `{repo} GH_TOKEN` (where `{repo}` is the repo name).
4. Make sure the "Selected Scopes" are `repo` and all sub-scopes, but nothing else.
5. Copy the token UUID, and prepend `GH_TOKEN=` to this. You should end up with something like `GH_TOKEN=d9167f44-edfc-4eb3-b0d3-310b7e75cb40` on your clipboard.
5. In the repository folder (on a Mac), run `pbpaste | travis encrypt -r chaijs/{repo}` (where `{repo}` is the repo name)
6. This will output something like the following:
   ```
   Please add the following to your .travis.yml file:
   secure: "QEQUy9IvdWbxcMTub3VvH4Ru2sCI3Ze/bWJ2pammucjQ1u1hqfeJf3NAFOlfrbpx52xlIiqgBwm6u2sDRZ69sLYkak/je5GCtE9rLhxoqiS1l6GlRZ9qnBrW7e790ja4aJdjeazULE3F6kgJwcy8E3qLA5eQOt9kdzevSU50AIQ="
   Pro Tip: You can add it automatically by running with --add.
   ```
7. (Pro Pro Tip: Dont use `--add` because it reformats the `.travis.yml` and strips comments. No fun.)
8. Copy the `secure:` bit, and add it to the array of `env.global` in the `.travis.yml`. Make sure to add a comment mentioning that this is the GH_TOKEN.
9. Submit a PR to the respective repository.
