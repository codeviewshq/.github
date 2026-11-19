# Node.js project setup

Use Node.js `26.13.1` and its bundled npm `11.20.0` for CodeView Node projects.

1. Add an exact `.node-version` containing `26.13.1`. In WSL, run `fnm install` and `fnm use` from the project root.
2. Add these fields to the root `package.json`.

   ```json
   {
     "packageManager": "npm@11.20.0",
     "devEngines": {
       "runtime": { "name": "node", "version": "26.13.1", "onFail": "error" },
       "packageManager": { "name": "npm", "version": "11.20.0", "onFail": "error" }
     }
   }
   ```

3. Run `npm install` to create `package-lock.json`, commit it, and use `npm ci` for repeat installs.
4. Add the **CodeView Node CI** workflow from the organization's starter workflows. Use the same Node patch in every Docker build and runtime stage when applicable.

Update the starter workflow, project pins, and Docker images together when changing the approved toolchain.
