# `json-server` Setup

Check out the [docs](https://github.com/typicode/json-server) for `json-server` to see everything you can do with it!

First, make sure you have `json-server` installed as a dependency for your project. In the same directory as your React code, run:

```
npm install json-server
```

Then, create a `db.json` file your React project directory **outside** the `src` folder (it should be separate from your React code). The `db.json` file should have an object with keys pointing to arrays of all the data you'll need for your app.

Make sure your JSON syntax is [valid](https://www.w3schools.com/js/js_json_syntax.asp), in particular check that your keys all have double-quotes around them and all your strings are also defined using double quotes.

```json
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" },
    { "id": 2, "title": "etc", "author": "typicode" },
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 },
    { "id": 2, "body": "another comment", "postId": 1 },
  ],
}
```

Then, run `json-server --watch db.json --port=3001` to run json-server on port 3001 (so it doesn't conflict with your React project).

You can also update the start script in your `package.json` file if you'd like an easy way to run `json-server` at the same time as React:

```json
"scripts": {
  "start": "json-server --watch db.json -p 3001 & react-scripts start && fg",
  ...
}
```
