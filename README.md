# DFD Hugo Module Starter

[![Netlify Status](https://api.netlify.com/api/v1/badges/1f8ccf5e-d791-41eb-b8a4-0f41b4ea4112/deploy-status)](https://app.netlify.com/sites/hugo-dfd-module-starter/deploys)

A starter repo for building Hugo modules (by Daniel F. Dickinson)

## Features

* Hugo module
* exampleSite (for demo deploys and/or documentation)
* Netlify-ready
  * Cache resources folder (exampleSite)
  * HTML Validation
  * Check internal links
  * HTML Minification

## Not a Theme

**Note:** This is not a theme, or even a theme component (although it could the basis for one).
This is a Hugo module skeleton, but with useful defaults for many of the files you will need in an
actual module.

## Using the Starter

### Create new repo for module

1. Download an archive of ``hugo-dfd-module-starter``.
   * Latest version of the ``main`` branch:
     * ZIP: <https://github.com/danielfdickinson/hugo-dfd-module-starter/archive/refs/heads/main.zip>
     * Tarball: <https://github.com/danielfdickinson/hugo-dfd-module-starter/archive/refs/heads/main.tar.gz>
   * Or the latest release (currently 0.1.2):
     * Tarball: <https://github.com/danielfdickinson/hugo-dfd-module-starter/archive/refs/tags/0.1.2.tar.gz>
     * Or ZIP: <https://github.com/danielfdickinson/hugo-dfd-module-starter/archive/refs/tags/0.1.2.zip>
2. Create a directory (for example ``hugo-dfd-responsive-images``)
3. ``cd hugo-dfd-responsive-images``
4. Extract the archive into this directory (e.g. ``unzip /path/to/downloaded/main.zip``)
5. Edit ``README.md``, ``LICENSE``, ``go.mod``, ``netlify.toml`` and ``exampleSite/README.md``, ``exampleSite/LICENSE``, ``exampleSite/config.toml``, ``exampleSite/go.mod`` with the information applicable to your module.
6. ``git init``
7. ``git checkout -b main`` (this is optional)
8. ``git branch -D master`` (only execute if you use 7. above)
9. (optional) ``git lfs install``
10. ``git add .``
11. ``git commit``
12. Create a GitHub repo (e.g. I used ``hugo-dfd-responsive-images`` which resulted in a URL of <https://github.com/danielfdickinson/hugo-dfd-responsive-images> (don’t add a README, LICENSE, and so on as the repo already has all that, and we want a bare repo for pushing our new module).
13. ``git remote add origin https://github.com/danielfdickinson/hugo-dfd-responsive-images.git``
14. ``git push origin --set-upstream main``
15. After a few moments you should see the code for your repo on GitHub (in the web interface).

### Connect repo with Netlify (for CI)

Prerequisite: You have already setup the Netlify app for you GitHub user or organization and are either allowing Netlify access to all your repositories or you have allowed Netlify access to this repo.

1. Login to Netlify
2. Select 'New Site from Git'
3. Select 'GitHub'
4. Select this repository from the list
5. If you are using Git-LFS, Select 'Advanced' and add variable ``GIT_LFS_ENABLED`` with value ``1``.
6. Select 'Deploy Site'
7. If you want to watch deploy progress, right click over the deploy and select "open in new tab" in your browser.
   1. If the deploy was not successful, correct any errors, commit and push, which should trigger another attempt at deploying.
8. Once the deploy is successful, select 'Site Settings' and 'Domain Management'
9. Beside the default Netlify random-site-name.netlify.app name select 'Options' and 'Edit site name'.
10. Rename the site (will always end in .netlify.app).
11. If you want a custom domain name and have a DNS service other than Netlify, then sign on to you provider and set a CNAME from your new-domain-name.example.com to your-netlify-domain-name.netlify.app.
    1. Trigger a deploy (otherwise the old name will interfere with the new name)
    2. If you have Netlify DNS you can skip this step
    3. Select 'Add custom domain'
    4. Enter the custom domain name from above.
    5. Select add the domain.
    6. Under HTTPS select 'Verify DNS configuration'
    7. Select 'Provision certificate'
    8. Wait
    9. You should now have an SSL protect version of the demo site for you repo.
12. Tweak any other settings as you wish.

### (Optional) Set up 'branch protection'

1. On GitHub, for you repo, go to Settings|Branches and enable 'branch protection' (Add rule, and enter 'main' as the branch)
   1. Check 'Require status checks to pass before merging'
   2. Check 'Require branches to be up to date before merging'
   3. Select 'Require linear history'
   4. Select 'Include administrators'
   5. Select 'Create'
2. In your repo create a new pull request branch (can have any name).
3. In Netlify go to Site Setting and copy the 'Site Badge' code
4. Paste site badge code into your README
5. Save and commit the change.
6. Push the new pull request branch to GitHub
7. Create a new pull request from the branch on GitHub
8. Once the deploy preview succeeds, open a new tab for 'Settings|Branches'
9. Select 'Edit' on you current 'main' branch protection rule
10. Search for statuses using the name of your repo
    1. You want at least:
       1. netlify/your-repo/deploy-preview
    2. All but 'changed pages' is recommended
11. Click 'Save Changes'
12. Close that tab
13. Back on the Pull Request (PR), Select 'Squash and Merge'
14. Confirm 'squash and merge'
15. Delete branch
16. Back in Netlify check the deploy status; it should succeed
17. On GitHub check your repository's README; it should show a Netlify status of 'Success'

### Develop Your Module

You are now ready to develop your module.
Hack away!
