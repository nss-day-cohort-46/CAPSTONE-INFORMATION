# Setting up your capstone application

Please read through all the instructions thoroughly before starting and reach out and ask questions if you are unsure about anything!

### Initial Setup

1. In the directory that you want to create your application, run `npx create-react-app the-name-of-your-app`.
1. `cd` into the application directory that has been created.
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

**Before starting this, make sure you have added, commited and pushed up your current branch. Then checkout a new branch from the main branch.**

Make sure you are in the root directory of your application and run the following command:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/nss-day-cohort-44/CAPSTONE-INFORMATION/main/scripts/auth.sh)"

```

Place this in your main app React component (i.e., App.js, Kennel.js, etc.)
Make sure to add import statements for `Route` and `Redirect` from `react-router-dom`. And import the Login and Register components.

```js
        <Route render={() => {
          // The user id is saved under the key app_user_id in local Storage. Change below if needed!
            if (localStorage.getItem("app_user_id")) {
                return (
                    <>
                        //Components that are rendered when the user is authenticated go inside this React fragment
                    </>
                )
            } else {
                return <Redirect to="/login" />
            }
        }} />

        <Route path="/login" render={props => <Login {...props} />} />
        <Route path="/register" render={props => <Register {...props} />} />
    </>
```

### Github Workflow

- Please make sure you are always working on a branch and commit very, very often.
- Keep your commits and pull requests small and manageable.
- Remember to push up on your branch any time you will step away from your machine. Remember, if it's on Github, we can always find a way to get it back in case of a sticky situation.
