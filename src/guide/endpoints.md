# API Endpoints

Here you can find a list of all the endpoints that are currently available in RobloxWrap. If you're looking for a specific endpoint, you can use the search bar to find it.

They are all split up into their respective categories, have fun!

:::tip TIP - Identifying authentication requirements on endpoints
There are icons next to each endpoint, these are used to indicate whether a endpoint requires you to login or not: 
- 🔓 - No login required
- 🔒 - Login required
:::

:::tip TIP - Optional arguments and object structures
On endpoints that take a arguments, you might see a `?` at the start of the argument name, this means that the argument is optional.

Furthermore, if the argument is a `object` type you will see how it is formatted in the example, `|` is used to separate the different opinions that can be used.
:::

## Users

### getUserInfo (🔓)

Takes a UserID as a number and returns a JSON object containing the user's profile details.

```javascript
getUserInfo(userId: number)
```

:::tip TIP
`displayName` will be `null` if the user has not set a display name.
It is best practice to use a ternary operator to check if the user has a display name set, and if not, use their username instead, like so:

```javascript
const response = getUserInfo(113260028);
console.log(displayName ? displayName : username);
```
:::

:::details Example
```javascript
getUserInfo(113260028)
```

```javascript
{
	username: 'WaviestBalloon',
	displayName: null,
	previousUsernames: [],
	description: "Hi, I'm Waviest, I'm a girl who loves all things computational. 🏳️‍⚧️👩‍💻\n" +
		'You might know of me in the Sci-Fi community.\n' +
		"Not everything I do is in Lua, I mainly code in JavaScript/TypeScript in Node.JS, I've started to learn Rust. I started playing on this platform since 2014-2015",
	avatarUrl: 'https://t4.rbxcdn.com/aec1839d24079d02ef48c0bb502bc153',
	userId: 113260028,
	banned: false,
	verified: false,
	joinDate: '2016-03-06T16:16:31.557Z',
	joinDateEpoch: 1457280991557
}
```
:::

### getUserThumbnail (🔓)

Takes a UserID as a number and returns a string with the thumbnail URL on Roblox's CDN.

`details` is an optional object that can be used to customise the thumbnail and is formatted like so: 
```js
{
	format: "png" | "jpeg",
	size: "30x30" | "48x48" | "60x60" | "75x75" | "100x100" | "110x110" | "140x140" | "150x150" | "150x200" | "180x180" | "250x250" | "352x352" | "420x420" | "720x720",
	isCircular: true | false
}
```

```js
getUserThumbnail(userId: number, ?details: object)
```

:::details Example
```javascript
getUserThumbnail(113260028, {
	format: "png",
	size: "420x420",
	isCircular: true
})
```

```javascript
"https://tr.rbxcdn.com/6a056e6626bec2ee3a741a49d7d91188/420/420/AvatarHeadshot/Png/isCircular"
```
:::

## Groups

### postShout (🔒)

Posts a shout to a group wall.

```javascript
postShout(groupId: number, messageShout: string)
```
:::tip TIP
Setting the `messageShout` argument to `null` will delete current group shout.
:::

:::details Example
```javascript
postShout(116048183, "Hello, meow!")
```

```javascript
{
	shout: 'Hello, Meow!',
	filtered: false,
	poster: {
		username: 'WaviestBalloon',
		displayName: null,
		description: "Hi, I'm Waviest, I'm a girl who loves all things computational. 🏳️‍⚧️👩‍💻\n" +
		'You might know of me in the Sci-Fi community.\n' +
		"Not everything I do is in Lua, I mainly code in JavaScript/TypeScript in Node.JS, I've started to learn Rust. I started playing on this platform since 2014-2015",
		avatarUrl: 'https://t6.rbxcdn.com/6a056e6626bec2ee3a741a49d7d91188',
		userId: 113260028,
		banned: false,
		verified: false,
		joinDate: '2016-03-06T16:16:31.557Z',
		joinDateEpoch: 1457280991557
	},
	created: '2023-01-11T11:38:57.723Z',
	createdEpoch: 1673437137723,
	updated: '2023-03-25T00:24:59.3833877Z',
	updatedEpoch: 1679703899383
}
```
