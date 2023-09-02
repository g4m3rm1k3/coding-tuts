## Notes
[![Next](https://d604h6pkko9r0.cloudfront.net/wp-content/uploads/2021/03/29113740/nextjs-cover.jpg)](https://nextjs.org/)
## Manual install

open project folder and run `npm install next react react-dom`

### layout

create new folder named app and inside that create a layout.jsx file
this is a template that will be applied to all pages
![[Pasted image 20230808042735.png]]

layout.jsx is the root element for the project so you must set it up in this way
```js
export default function RootLayout() {
  return (
    <html lang='en'>
      <body></body>
    </html>
  );
}
```
this component must return the children so add the prop and display it
here I use destructuring
```js
export default function RootLayout({ children }) {
  return (
    <html lang='en'>
      <body>{children}</body>
    </html>
  );
}
```
in the node modules folder theres a file call .bin that npm puts all the commands that are installed with our packages
```
ls node_modules/.bin  
```
![[Pasted image 20230808043830.png]]
There is a command *next* npx automatically finds it in the correct folder if we run `npx next --help` it prints instructions
![[Pasted image 20230808044416.png]]
we are currently intersted in the **dev** command which starts a server on our machine
`npm next dev`
![[Pasted image 20230808044542.png]]
the next command creates a folder in the directory
![[Pasted image 20230808044740.png]]
we should create a .gitignore file and add /.next/ and /node_modules/ to this folder
```
/.next/
/node_modules/
```

We need to create a new page in the app folder called page.jsx
![[Pasted image 20230808045029.png]]
the page.jsx must have a default export I set it up this way
```js
export default function HomePage() {
  return <h1>My first Next.js page</h1>;
}
```
next open the package.json file and add a script "dev":"next dev" like this
```js
{
  "name": "next-reviews",
  "private": true,
  "scripts": {
    "dev": "next dev"
  },
  "dependencies": {
    "next": "^13.4.13",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  }

}
```
Now we can run `npm run dev` from the terminal to start a local server and run our project
lets update our layout.jsx component to best practices
```jsx
export default function RootLayout({ children }) {

  return (
    <html lang='en'>
      <body>
        <header>[Header]</header>
        <main>{children}</main>
        <footer>[Footer]</footer>
      </body>
    </html>
  );
}
```
The layout is a templlate that will apply to all the pages

---
## Page Routing

Next js uses file based routing each nested folder has a page.jsx or a page.tsx and the url follows the layout of the folder structure
![[Pasted image 20230809045543.png]]
![[Pasted image 20230809045558.png]]
![[Pasted image 20230809045638.png]]
In VScode you can use the command `ctr+p` to find a page quickly, but with all the pages being names page.jsx you have to look at the path next to the page. 
![[Pasted image 20230809053718.png]]
The difference between App Router and Page Router can be seen here
![[Pasted image 20230809053821.png]]
With App router we can place multiple files in the same folder

## Next help
```console
npx next --help
    Usage
      $ next <command>

    Available commands
      build, start, export, dev, lint, telemetry, info, experimental-compile, experimental-generate

    Options
      --version, -v   Version number
      --help, -h      Displays this message

    For more information run a command with the --help flag
      $ next build --help
```

add the scripts to build production, and start to start production to the package.json file
```js
{
  "name": "next-reviews",
  "private": true,
  "scripts": {
    "build": "next build",
    "dev": "next dev",
    "start": "next start"
  },
  "dependencies": {
    "next": "^13.4.13",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  }
}
```
run npm run build to build the optomized build for production
```console
npm run build
> build
> next build

- info Creating an optimized production build
- info Compiled successfully
- info Linting and checking validity of types
- info Collecting page data
[    ] - info Generating static pages (0/7)[HomPage] rendering
- info Generating static pages (7/7)
- info Finalizing page optimization

Route (app)                                Size     First Load JS
┌ ○ /                                      861 B          79.1 kB
├ ○ /about                                 151 B          78.4 kB
├ ○ /reviews                               150 B          78.4 kB
├ ○ /reviews/hollow-knight                 152 B          78.4 kB
└ ○ /reviews/stardew-valley                151 B          78.4 kB
+ First Load JS shared by all              78.2 kB
  ├ chunks/596-95c3f4f1940bef62.js         25.9 kB
  ├ chunks/fd9d1056-03be6752d46af311.js    50.5 kB
  ├ chunks/main-app-a6bf45eca9dd2113.js    214 B
  └ chunks/webpack-bf1a64d1eafd2816.js     1.61 kB

Route (pages)                              Size     First Load JS
─ ○ /404                                   182 B          74.9 kB
+ First Load JS shared by all              74.7 kB
  ├ chunks/framework-8883d1e9be70c3da.js   45 kB
  ├ chunks/main-b426692aacdf8ee8.js        27.8 kB
  ├ chunks/pages/_app-52924524f99094ab.js  195 B
  └ chunks/webpack-bf1a64d1eafd2816.js     1.61 kB

○  (Static)  automatically rendered as static HTML (uses no initial props)

```
This generates a root for each page in the project
the circle means its a static page
![[Pasted image 20230816051307.png]]
run npm start to start the server
```console
npm start
> start
> next start

- ready started server on 0.0.0.0:3000, url: http://localhost:3000
```
Lets create a Nav in the root layout.jsx file
```jsx
import Link from 'next/link';

export default function RootLayout({ children }) {
  return (
    <html lang='en'>
      <body>
        <header>
          <nav>
            <ul>
              <li>
                <Link href='/'>Home</Link>
              </li>
              <li>
                <Link href='/reviews'>Reviews</Link>
              </li>
              <li>
                <Link href='/about'>About</Link>
              </li>
            </ul>
         </nav>
        </header>
        <main>{children}</main>
        <footer>[Footer]</footer>
      </body>
    </html>
  );
}
```
prefetch
to disable prefetch on a link add the 
```jsx
<Link href="/about" prefetch={false}>About</Link>
```
