# Mod 4 React Guided Project 

You've made it! You're ready to build a React application! We're going to be building the app from scratch, following the guidelines from [Thinking in React](https://reactjs.org/docs/thinking-in-react.html) to build your project incrementally.

## Requirements

- React frontend
- Rails backend, or `json-server` (talk to your instructors)
- User stories to handle at least 4 different CRUD actions on your models

## Phase 1: Planning

**This should take no more than half a day**.

Before writing any code, let's come up with a game plan. Start by thinking of the Minimum Viable Product (MVP) version of your app, since that's what you'll be building first. You'll need to pitch your project to your instructors and be approved before writing any code.

For your MVP pitch, you should have the following:

- **Elevator Pitch**: 1 - 2 sentence description of your app's functionality
- **User Stories**: at least 4 user stories related to CRUD actions
- **Wireframes**: a sketch of what your MVP should look like (can be hand-drawn, or using whiteboarding tools like [awwapp](https://awwapp.com/) etc)
- **Component Hierarchy**: a breakdown of what components you will need, based on your wireframes
- **Domain Model**: what models you'll need to represent your user stories, and what the relationships between those models is
- **(optional) Sample JSON data**: how you'd like the data in your application formatted, for example:

```json
// users
{
  "id": 1,
  "username": "ian123",
  "bio": "Lead Instructor, Flatiron School"
}

// posts
{
  "id": 1,
  "title": "How to think in React",
  "body": "Lorem ipsum",
  "user_id": 1
}
```

After planning, make a copy of the [Project Pitch Template](https://docs.google.com/document/d/1XBMoO3fDcF_c8tyQwUnOXWWrmnFg_tpP2i7o66dakFc/edit#), fill it out, and Slack it to your instructors for approval.

## Phase 2: Static Site

**This should take about half a day**.

To create your React project, you may use a tool called [create-react-app](https://github.com/facebookincubator/create-react-app), an awesome project generator developed by Facebook. To use this, in the directory where you'd like to create your project, `npx create-react-app my-project-client`. It's that simple!

We'd recommend to begin by removing any of the default files and code given to you by Create React App that you do not understand.

Once you've created the project repo, start by working on building out your component hierarchy based on the wireframes from Phase 1.

At this point, your components shouldn't have any state or user events. To get some seed data into your app, you can pull in some sample data into a file by importing a `.json` file, like this:

```jsx
import React from 'react'
import UserItem from './UserItem'

// pull in an array of JSON data
import users from '../data/users.json'

class UserContainer extends React.Component {
  render() {
    return (
      <ul>
        {/* pass down each user as a prop */}
        {users.map(user => <UserItem key={user.id} user={user} />)}
      </ul>
    )
  }
}
```

Building your site this way will force you to think about how your data should be structured, so once you start work on the backend you will have a better sense of what your models will look like and how to format data in your responses.

Don't worry too much about styling at this point! It's OK if your site doesn't match exactly with the look of your wireframes, as long as you have the right component hierarchy.

The following are some really great resources on how to think about setting up a React project (_Spoiler: They both say the same thing, "There's no right answer!"_)

* [React Docs](https://github.com/reactjs/reactjs.org/blob/71788c647daa07392a8156609fdbede8e9ed24f7/content/docs/faq-structure.md) This was written by Dan Abramov himself <3 <3 <3....
* [The 100% Correct Way to Structure a React App (or why there’s no such thing)](https://hackernoon.com/the-100-correct-way-to-structure-a-react-app-or-why-theres-no-such-thing-3ede534ef1ed)

## Phase 3: Add State & Event Handling

**This should take one day**.

Once you have the static version of your site built out, figure out which of your user stories will require state. Think about these questions from [Thinking in React](https://reactjs.org/docs/thinking-in-react.html) to determine where you need state:

1. Is it passed in from a parent via props? If so, it probably isn’t state.
2. Does it remain unchanged over time? If so, it probably isn’t state.
3. Can you compute it based on any other state or props in your component? If so, it isn’t state.

Then, figure out where state should live in your component hierarchy:

1. Identify every component that renders something based on that state.
2. Find a common owner component (a single component above all the components that need the state in the hierarchy).
3. Either the common owner or another component higher up in the hierarchy should own the state.
4. If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

Next, set up some user events so you can update state based on user interaction (i.e. submitting a form, clicking a button, etc.). If necessary, add inverse data flow to pass data up from child components to parents that need it.

At this point, you should have a version of your site done that fully represents your project's MVP, without any backend persistence. Great work getting this far!

## Phase 4: Review

Once you've built out the static version of your site and added state, schedule a review with your instructors. They'll look at:

- Your component hierarchy
- Where your state is located
- Proper use of props to pass down data
- Inverse data flow with callback functions
- Making controlled forms
- Function vs Class components

After review, you can start working on the next steps.

## Phase 5: Backend and Client-Server Communication

By building out your static site you should now have a great sense of how you would like your data structured in the frontend.

Depending on how much time there is left for your project, your instructors will either ask you to build out a Rails API for the backend or to use `json-server` as a simpler option.

You can find [Rails setup instructions here](RAILS.md) and [`json-server` instructions here](JSON-SERVER.md).

Remember, running `rails new` will create a new Git repository, so make sure you are in a different directory from your React application when you create your Rails app.

Once you have your backend set up with some seed data, make sure you are able to fetch that data from your frontend. Then, work on building out your CRUD features so that they persist to the backend. Think about when you'll need to request data from the backend (component lifecycle methods), and when you'll need to send data to the backend (user events).

## Phase 6: Freedom!

Now that you have your frontend and backend set up, start working on some more advanced features! Some things you can consider adding to your project:

* Client-side routes with [React Router](https://reactrouter.com/web/guides/quick-start)
* [Auth](https://github.com/ihollander/rails-react-auth-lecture)
* Integrating an external API
* Styling using a framework like [Semantic](https://react.semantic-ui.com/) or [Bootstrap](https://react-bootstrap.github.io/)
* Or custom css using [stylesheets](https://create-react-app.dev/docs/adding-a-stylesheet), [sass](https://create-react-app.dev/docs/adding-a-sass-stylesheet), or a CSS-in-JS library like [Styled Components](https://styled-components.com/)

There are a lot of great React libraries out there, so feel free to experiment - just make sure you create a new branch on your repo any time you're testing out a new library.

## Notes

By default both your client app and your rails app will run on port 3000. You'll have to specify one or the other to run on a separate port.

* Rails: `rails s -p 3001`
* json-server: `json-server --watch db.json --port 3001`
* React: Check out this [Stack Overflow](https://stackoverflow.com/a/50869504)

It is highly suggested that any calls to 3rd party APIs are made _through your backend_.

Example: A user clicks a button that says 'Get Gifs'
* React makes a request to Rails
* Rails makes a request to the Giphy API
* Rails receives the response from Giphy and sends to React
* React receives the response from Rails and you do something with it on the client

This is so you can avoid any *CORS* issues. If you are unable to hit an API from your React app due to a CORS restriction, it is very likely that it is impossible to do so. _Brief Refresher on CORS: the idea is that from one domain (the port your webpack development server is running on) you are not allowed to access another domain.  You must make the request from a server (i.e. Rails), so the request is exempt from the Same-Origin Policy restriction._
