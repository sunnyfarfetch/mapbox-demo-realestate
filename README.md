<<<<<<< HEAD
# public-tools-and-demos

This monorepo contains several public-facing Mapbox demos and developer tools, along with a library of common react components.

This purpose of this repo is to establish a framework for what makes a good public-facing demo, and include re-usable UI components to standardize the look and feel of these demos for a more seamless presentation.  This is an initiative of the Developer Relations Team.

## Architecture

Each project included in this repo is a react vite app.  React projects allow us to make use of reusable components, such as the UI components in `demo-components`, as well as `@mapbox/mr-ui` which includes buttons, icons, and other complex components used in Mapbox Studio, the Mapbox Docs, and other frontend things.

## Local Development

We use yarn workspaces to allow projects to consume shared components without having to publish them as a package to npm.  

After cloning the repository, install dependencies with `yarn`:

```
> cd public-tools-and-demos && yarn
```

This will install dependencies at the top level of the monorepo as well as in the individual project directories.

Next, cd into the project directory you would like to work on, and start the dev server:

```
> cd projects/what-the-tile && yarn dev
```

## Shared Components

The shared components in `projects/demo-components` are not transpiled or published to npm. They are intended for local use and can be imported via the package name `mapbox-demo-components`.  `mapbox-demo-components` does not have to be included in the consuming project's `package.json` (this is a feature of yarn workspaces).

```
 import { header } from 'mapbox-demo-components'
```

## Moving a Vanilla JS Site into a React Project

Vanilla JS examples can be quickly ported into a react site though the use of iframes.  See the `developer-cheatsheet` project for an example of this pattern. 

## Base Site URL

Deployments to `labs.mapbox.com` require the react app to serve content from a subdirectory.  This is accomplished via the `base` property in `vite.config.js` in each project directory.

For example, if the site will be hosted at `labs.mapbox.com/my-project`, set `base` to `/my-project`:

```
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: '/my-project'
})
```

Be sure to add the `import.meta.env.BASE_URL` globally injected variable when referencing static assets like images and iframes:

```
<div
  className='bg-cover h-80 lg:h-80 '
  style={{
    backgroundImage: `url("${
      import.meta.env.BASE_URL
    }/${imageUrl}")`
  }}
/>
```

## Public AccessToken

All projects should use the common accessToken from the `labs-sandbox` account, which can be imported from `demo-components`.  For projects that only need the access token to instantiate a map or add `mapbox-gl-geocoder`, this is handled for you in the `Map` component.

```
import AccessToken from 'demo-components'
```
=======
# mapbox-realestate
>>>>>>> origin/main
