# rollup-watch-error

Simple reproduction:

1.) Start rollup watch with `yarn watch` will output :
  ```
  rollup v0.58.2
  bundles a.js → out.js...
  (!) Unresolved dependencies
  https://github.com/rollup/rollup/wiki/Troubleshooting#treating-module-as-external-dependency
  http (imported by b.js)
  created out.js in 42ms

  [2018-05-02 15:42:21] waiting for changes...
  ```
  
2.) While watching, change `a.js` to get this result:
  ```
  rollup v0.58.2
  bundles a.js → out.js...
  [!] Error: Could not load http (imported by /path/to/b.js): ENOENT: no such file or directory, open 'http'
  Error: Could not load http (imported by /path/to/b.js): ENOENT: no such file or directory, open 'http'
      at /path/to/node_modules/rollup/dist/rollup.js:20561:19
      at <anonymous>
      at process._tickCallback (internal/process/next_tick.js:188:7)
  ```
