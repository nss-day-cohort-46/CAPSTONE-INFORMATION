# Setting up your capstone application

Please read through all the instructions thoroughly before starting and reach out and ask questions if you are unsure about anything!

### Initial Setup

**If your repository is empty:**

1. In the directory that you want to create your application, run `npx create-react-app the-name-of-your-app`.
1. `cd` into the application directory that has been created.

**OR if you repo is not empty (it has a `clone` button available):**

1. Clone down your repo.
1. `cd` into your repo.
1. Run `npx create-react-app .`.

**Once your React application has been created, follow the rest of these steps:**

1. Add `.eslintcache` to the bottom of your `.gitignore`.
1. Open your `README.md` and delete all text in the file.
1. Add and commit your changes on `main`.
1. Go to your empty capstone repository on Github and follow the instructions under the heading **…or push an existing repository from the command line** (The second set of instructions!)
1. Refresh your repo in your browser to make sure your repo now contains your application.
1. In your terminal, make sure to checkout a branch before you start working.

### Persistent storage with JSON-SERVER

You can set up your json-server API to be a part of your application directory (like Glassdale) or a separate directory (like Kennel). If you decide to keep your API a separate directory, make sure to create a new repository for it and push it up.

### Routing

If you plan to use routing in your application, in your application root directory, run `npm i --save react-router-dom` to install the package.

### Authentication

**Before starting this, make sure you have added, committed and pushed up your current branch. Then checkout a new branch from the main branch.**

Make sure you are in the root directory of your application and run the following command:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/nss-day-cohort-46/CAPSTONE-INFORMATION/main/scripts/auth.sh)"

```

In `index.js`, make sure to have `import { BrowserRouter as Router } from "react-router-dom"` and wrap your application component in `<Router></Router>`.

Place this in your main app React component (i.e., App.js, Kennel.js, etc.)

```js
    <Route render={() => {
        if (sessionStorage.getItem(userStorageKey)) {
          return (
            <>
              //Components that are rendered when the user is authenticated go inside this React fragment
            </>
          )
        } else {
          return <Redirect to="/login" />;
        }
    }} />

    <Route path="/login">
      <Login />
    </Route>
    <Route path="/register">
      <Register />
    </Route>
```

And the following import statments at the top of the component:

```js
import { Route, Redirect } from "react-router-dom"
import { Login } from "./auth/Login"
import { Register } from "./auth/Register"
import { userStorageKey } from "./auth/authSettings"
```

*The `Register` and `Login` components assume your local JSON Server is running at port 8088 and that you have an endpoint for `users`. Both of these can be changed in the `authApi.js` in the `auth` directory.*

### API Keys

## Settings.js & Settings.js.example

If you are using any API keys, make sure you add the files with the API keys to your `.gitignore`:


1. Add `Settings.js` to your `.gitignore`.
1. Create a `Settings.js.example` from which you will be exporting your API keys:

```js
export const testAPI = {
  baseURL: "THE API URL",
  apiKey: "THE API KEY"
}
```

**DO NOT PUT YOUR ACTUAL API KEYS IN Settings.js.example!!!.**

1. Add, commit and push to Github.
1. Make a copy of the `Settings.js.example` file and remove the .example extension.

**DO NOT PUSH UP YOUR API KEYS TO GITHUB.**

This means don't put your API keys in issues, cards on the project board, pull requests, comments, the `Settings.js.example` file, the README, etc. API keys need to be kept out of anything that can be accessed on Github.

The one and only place the API keys should be in is your `Settings.js` file.

## Environment Variables

If you interested in using a `.env` file **instead** of `Settings.js`, please read through the [documentation](https://create-react-app.dev/docs/adding-custom-environment-variables/%23adding-development-environment-variables-in-env): 

1. The `.gitignore` already contains several `.env` files but if your file has a name that is not listed in the `.gitignore`, be sure to add it.
1. You will still need to have a `.example` file. (And it **should not** contain your API keys, just a placeholder.)

### Github Workflow

- Please make sure you are always working on a branch and commit very, very often.
- Keep your commits and pull requests small and manageable.
- Remember to push up on your branch any time you will step away from your machine. Remember, if it's on Github, we can always find a way to get it back in case of a sticky situation.
