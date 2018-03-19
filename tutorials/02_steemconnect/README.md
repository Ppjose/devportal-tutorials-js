Steemconnect is unified authentification system built on top of Steem built in collaboration of Busy.org and Steemit Inc.
Layer to ensure easy access and setup for all application developers as well as secure way for users to interact with Steem apps.

Setting up Steemconnect in your app is straight-forward process and never been this easy.

### Step I

1. Visit [Steemconnect Dashboard](https://steemconnect.com/dashboard) and login with your Steem credentials
2. You will see Applications and Developers section, in Developers section click on `My Apps`
3. Create New App using Steemconnect, which will help you create new Steem account for your application. Let's call it `demo-app` for this tutorial purpose. Account creation fee will be deducted from your balance, make sure you have enough funds to complete account creation.
4. Give your app name, description, icon image link, website (if available) and Redirect URI(s)

Redirect URI(s) will be used within your application to forward user after authentification is successful. This is typical backend web development, we hope you know how to set up.


### Step II

Once you have setup account for new application, you can setup application with Steemconnect authentification and API processes.
To do that, you will need to install `sc2-sdk` nodejs package with `npm i sc2-sdk`.
Within application you can initialize Steemconnect

##### Initialize
> `app` - is account name for application that we have created in Step I.3, `callbackURL` - is Redirect URI that we have defined in Step I.4, `scope` - permissions application is requiring/asking from users


Now that `sc2-sdk` is initialized we can start authentication and perform simple operations with Steemconnect.

##### Login URL

> Returns login URL which will redirect user to sign in with Steem connect screen. Successfull login will redirect user to Redirect URI or `callbackURL`. Result of successful login will return `access_token`, `expires_in` and `username` information, which application will start utilizing.

##### Request link

> Application can request returned link into popup screen or relevant screen you have developed. Popup screen will ask user to identify themselves with their username and password. Once login is successful, you will have Results

##### Result

> Returned data has `access_token` - which will be used in future api calls, `expires_in` - how long  access token is valid in seconds and `username` of logged in user.

##### Set token

> After getting `access_token`, we can set token for future Steemconnect API requests.

##### Get user info

> Users info can be checked with `me` which will return object
`account` - current state of account and its details on Steem blockchain, `name` - username, `scope` - permissions allowed with current login, `user` - username, `user_metadata` - additional information user has setup.

##### Logout

> In order to logout, you can use `revokeToken` function from sc2-sdk.

Learn more about [Steemconnect operations here](https://github.com/steemit/steemconnect-sdk)

### To run

* clone this repo
* `cd tutorials/02-steemconnect`
* `npm i`
* `npm run start`