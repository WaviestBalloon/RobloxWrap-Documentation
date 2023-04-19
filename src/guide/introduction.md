# Introduction 👋

Hello there Robloxian! Looking for a simple and easy way to interact with the Roblox API? Look no further, RobloxWrap is a API wrapper for almost anything Roblox-related, from creating a Group moderation bot to intergrating it with a Discord bot.

## Installation

Alright, let's get started, first we need to install the RobloxWrap package from the NPM registry, run the following command in your terminal:

```bash
npm i robloxwrap
```

:::tip TIP
Using it in multiple projects? Append the `-g` flag to install it globally, save the hassle of installing it every time.
:::

Congrats, you've installed RobloxWrap! Now let's get started with the basics.

## Getting started

### Creating the Client

The first thing we need to do is create a Client, this is the main class that will be used to interact with the API. It's pretty simple to do, just import the Client class and create a new instance of it:

```javascript
const RobloxWrap = require("robloxwrap");
const client = new RobloxWrap();
```

Now we have a Client instance, let's get started hook up a Event Listener and sign in.

### Obtaining and Authenticating with a Cookie

There are two things that are needed to authenticate, your `.ROBLOSECURITY` which is the cookie token used to send requests to the Roblox API, and your `X-CSRF-TOKEN` which is used to prevent Cross-Site Request Forgery attacks.

You won't need to worry about the `X-CSRF-TOKEN` as RobloxWrap will automatically generate it for you, but **you will need to provide the `.ROBLOSECURITY` cookie**.

**Let's obtain your `.ROBLOSECURITY` cookie:**

- Head to your Roblox homepage: [roblox.com](https://roblox.com)
- Open up the Developer Tools (`F12` / `Ctrl` + `Shift` + `I`)
- Go to the `Storage` tab
- Go to `Cookies` and find the `roblox.com` domain
- Find the `.ROBLOSECURITY` cookie and copy the value

:::warning SECURITY WARNING
**Never share your `.ROBLOSECURITY` authentication token** or any other form of token with anyone as it can be used to gain access to your account. If you think someone has your token, log out and then log back in to reset your tokens and as a extra precaution, change your password immediately.
:::

:::tip TIP
It is best practice to store your token in a environment file (`.env`), this way you can keep your token safe and not have to worry about it being leaked when editing your code or if you accidently commit your index file to a public repository. Use a package like [dotenv](https://npmjs.com/package/dotenv) to load your environment variables.
:::

### Updating our current code to login to Roblox

Okay, let's add a Event Listener to our Client and authenticate with our cookie token:

```javascript
const RobloxWrap = require("robloxwrap");
const client = new RobloxWrap();

client.on("authenticated", (response) => {
	console.log("Hello, World! I am " + response.username + " (" + response.userId + ")");
});

client.login(/* Your .ROBLOSECURITY cookie here! */);
```

Save it, then run it with `node <filename here>`.

:::details Expected output
If everything went well, you should see something like this:

```bash
Hello, World! I am [USERNAME] ([USERID])
```
:::

## Debugging potential errors

Sometimes, you may encounter an error when trying to authenticate with your cookie, here are some common errors and how to fix them: 

:::details TokenValidationError
- `Invalid token cookie, the token fails the basic checks`: This error is thrown when the token fails checks like datatype, length or matching against a regex. To fix this, log out of your account and log back in, this will generate a new token.
- `The account associated with the token has been moderated or banned`: This error is thrown when the account associated with the token has been moderated or banned. To fix this, reactivate your Roblox account associated with the token.
**If you don't have access to the account, you will need to contact Roblox Support.**
**Please don't open an issue on the GitHub repository if you encounter this error**, it's not a bug, we cannot help you. :(
- `Invalid token cookie, the token is not recognised by Roblox`: This error is thrown when the token is not recognised by Roblox. To fix this, log out of your account and log back in, this will generate a new token.
- `An unknown error occurred while verifying the token's validity`: Something went wrong while verifying the token's validity. If you encounter this issue constantly, [click here](https://github.com/WaviestBalloon/RobloxWrap/issues/new) to open a new Issue on the GitHub repository and be sure to post the error message details.
:::

:::details TokenError
This error is generic and only relates to `X-CSRF-TOKEN` generation.
- `An unknown error occurred while generating a CSRF token`: Something went wrong while trying to generate the CSRF token used for querying endpoints, Roblox might be down.
:::

:::details ClientError
This error is generic and relates to the Client class, for example, `Client.login` or internal issues. If you encounter this error, [click here](https://github.com/WaviestBalloon/RobloxWrap/issues/new) to open a new Issue on the GitHub repository.
:::

If you encounter any issues that are reoccurring and replicatable, [click here](https://github.com/WaviestBalloon/RobloxWrap/issues/new) to open a new Issue on the GitHub repository and be sure to post as much detail as possible. (Be sure not to include any sensitive information)
