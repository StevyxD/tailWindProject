1) Run the following command in the terminal:
npx tailwindcss init --full

This creates a file tailwind.config.js in the root directory i.e. same directory as package.json

2) Update the file content as follows:

module.exports = {
  content: [
    './public/**/*.{html,js}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

3) Run the following command in the terminal:
npm run build-css

4) Run the following command in the terminal:
npx tailwindcss -i ./src/styles.css -o ./public/styles.css --watch
##################
@apply directive issue

I had an issue where the card and badge classes were not being
copied over into the built CSS file (even if I just put a regular 
CSS rule like .card { background-color: white; }.

After reading many issues on the GitHub and StackOverflow
posts with no success, I finally figured out that I needed
to change the build script to say "tailwindcss build -i src/styles.css -o public/styles.css" 
(take not of the -i) because I was seeing a
 deprecation notice of not using the -i flag to point to the input. Maybe this will save someone else the trouble in the future.
##################
auto update

You can also run the command from the command line using "npx" (instead of adding to scripts in package.json):
npx tailwindcss build -i src/styles.css --output public/styles.css

And if you want to have it update as you edit (but give up the current terminal until you CTRL-C to exit out of it):
npx tailwindcss build -i src/styles.css --output public/styles.css --watch

An example of when that is useful is when you have live server started from VSCode - right click on index.html and start from there and not from your package.json in a concurrent fashion. But you have to double save - once again after the rebuild.

########
Use heroicon website for getting icons