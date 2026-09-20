---
title: 'Upgrading Bitbucket Authentication to API Tokens'
description: 'Guide on how to update Bitbucket Repo to use API Tokens'
pubDate: 'Sept 20 2026'
heroImage: '../../assets/blog-placeholder-3.jpg'
tags:
  - Bitbucket
  - Guide
---

Don't we all love it as developers when our tools change on us. Well for those who are using bitbucket you may have come across an error when trying to fetch or push into your exisiting repoistories. Atlassian have made a change that which means we have to use API Tokens instead of app passwords. 

As seen on  [Bitbucket changelog](https://developer.atlassian.com/cloud/bitbucket/changelog/#CHANGE-3222).

Bitbucket Cloud is deprecating App Passwords in favor of scoped API tokens. To ensure your Git operations in your IDE (i.e., Rider, Visual Studio, or VS Code) continue working without interruption on both Windows and macOS, please follow these steps to update your local environment.
You must perform these steps for your active repositories. Your commit history, author name, and profile attribution will remain completely unaffected by this change.

This guide will help you get yourself back on track.

## Step 1: Generate Your Scoped API Token on Bitbucket
To create and use an API token:

1. In Bitbucket Select your Profile icon, then select Account settings.
2. Select Security, then Create and manage API tokens, and then select Create API token.
3. Select Create API token with scopes.
4. Name the token, set an expiry date, select Bitbucket as the app
5. Assign the necessary scopes and save the token.
    - A good minimum for typical repository, pull request, and pipeline operations would be:
        - **Read**
            - read:repository:bitbucket
            - read:pullrequest:bitbucket
            - read:pipeline:bitbucket
        - **Write**
            - write:repository:bitbucket
            - write:pullrequest:bitbucket
            - write:pipeline:bitbucket
6. Click Create.
7. Copy the generated token immediately. Bitbucket will not display it a second time. 

## Step 2: Clear Cached Credentials
Operating systems and IDEs like to cache old authentication details. You will likely see two distinct, related entries created at the same time. You must delete both entries to prevent the system from trying to use your old App Password.

**Note:** Close your IDE completely before performing these steps to stop background processes from immediately regenerating the cache.

### For Windows Users

1. Open the Start Menu, search for Credential Manager, and open it.
2. Select Windows Credentials.
3. Scroll down to the Generic Credentials section.
4. Locate and remove every entry that begins with `git:https://bitbucket.org` 
- This includes variants such as:
    - `git:https://bitbucket.org`
    - `git:https://bitbucket.org/refresh_token`
    - `git:https://your-username@bitbucket.org/refresh_token`

5. Click on each entry and select Remove.

### For macOS Users

1. Open Spotlight (Cmd + Space), search for Keychain Access, and open it.
2. In the left sidebar under the Default Keychains section, select login. You must explicitly select this keychain category to successfully modify and delete these records.
3. In the top-right search bar, type bitbucket.org.
4. Locate both of the following entries:
    - IntelliJ Platform Git HTTP — `http://your-username@bitbucket.org` or `hg:https://your-usename@bitbucket.org`
    - bitbucket.org or `git:[https://bitbucket.org` (Used by the macOS Git CLI and VS Code)
5. Right-click each entry and select Delete.

## Step 3: Re-authenticate in your IDE 
1. Open your IDE
2. Trigger any remote Git action, such as Fetch or a Pull/Push operation.
3. A native login dialog will appear.
4. In the Username field, enter exactly: `x-bitbucket-api-token-auth` or your `username` (both should work)
5. In the Password field, paste the API Token you generated in Step 1.
6. Click Log In or OK.

Your environment is now securely updated and you can get back to coding.