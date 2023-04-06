## Secure Tokens

As part of Chai's standards, we use [Continuous Integration](https://en.wikipedia.org/wiki/Continuous_integration) and Semi Automated Deployment via GitHub Releases. To enable these to happen, we need to provide our CI server - [GitHub Actions](https://docs.github.com/en/actions) with the right environment variables to gain access to our Saucelabs accounts (for cross browser testing), Github account (for automatically posting release notes), and our NPM account (for publishing packages).

We cannot store these in plaintext, because that means anyone who had them could publish whatever they wanted through the chaijs user - for example overwriting the `chai` npm package with a virus. As such, we encrypt these tokens in the codebase.

### Who can access the real tokens?

The users in the [token-bearers](https://github.com/orgs/chaijs/teams/token-bearers) has access to https://github.com/chaijs/token-bearers repository which contains instructions to log into the `chaijs` npm account. If you need a token created or regenerated for your repository, you should @mention the token-bearers team, so they may generate some tokens for your repository.

### How are the tokens generated?

GitHub autoamtically generates GitHub tokens for each Actions build. For npm and saucelabs tokens, we must generate these manually for each package we wish to publish. The process is as follows:

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

1. Visit the [Granular Access Tokens page](https://www.npmjs.com/settings/chaijs/tokens/granular-access-tokens/new), you may be prompted to sign in as the Chaijs user - Token Bearers have the password and must not share it with anyone. If you're not a member of the Token Bearer's team, ask someone who is.
   *  (If you cannot access that URL, the way to get there as of writing is opening the menu where the profile image is, navigating to `Access Tokens`, opening the `Generate New Token` menu, and navigating to `Granular Access Token`).
2. In the field `Token Name` enter the package name, e.g. `chai-spies`.
3. In the field `Description` add "Release token for {}" where `{}` should be the package name, e.g. `Release token for Chai Spies`
4. Change the `Expiration` to 365 days
5. Ignore the `Allowed IP Ranges` section.
6. In `Packages and Scopes`, enable `Read and write`, and select `Only select packages and scopes`, then in the `Select packages and scopes` dropdown, you'll need to select the name of the package, e.g. `chai-spies`
  * The package won't be available if it has never been published. In that case, you'll need to select `All packages`, use that token to publish, then regenerate a fresh token scoped to the package, and delete the old one. Alternatively you can manually publish the package to register the name.
7. Ignore the `Organizations` section
8. Summary should read:
   > Provide **read and write** access to 1 packages and 0 scopes
   > Provide **no** access to organiizations
   > Expires on {date a year from now}
9. Click `Generate Token`
10. Where it says `Token successfully generated`, the token will be there to copy. It should start with `npm_` and have a bunch of alphanumeric characters after that.
11. now you need to put it into GitHub's Actions secrets store:
12. Visit https://github.com/chaijs/{}/settings/secrets/actions where `{}` is the name of your package, e.g. https://github.com/chaijs/chai-spies/settings/secrets/actions
   * (If you cannot access that url, the way to get there as of writing is visiting the repository page for that package, e.g. https://github.com/chaijs/chai-spies, navigating to `Settings`, opening the `Secrets and variables` menu, then navigating to the `Actions` submenu item.
13. From here navigate to the `New repository secret` button
14. In `Name` enter `NPM_TOKEN` exactly.
15. In `Secret`, paste the contents you copied from `Token successfully generated`.
16. Navigate to the `Add secret` button.
17. Finished!
