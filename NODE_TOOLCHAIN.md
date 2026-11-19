# Node.js project setup

Use Node.js `26.13.1` and pnpm `12.21.0` for CodeView Node projects.

1. Add a `.node-version` containing `26.13.1`. Run `fnm install` and `fnm use` from the project root in WSL.
2. Pin the tools in the root `package.json`.

   ```json
   {
     "packageManager": "pnpm@12.21.0",
     "engines": { "node": "26.13.1" }
   }
   ```

3. Set `pmOnFail: error` in `pnpm-workspace.yaml`. Run `pnpm install` to create `pnpm-lock.yaml`, commit it, and use `pnpm install --frozen-lockfile` for repeat installs.
4. Add **CodeView Node CI** from the organization's starter workflows. Use the same Node patch in every Docker build and runtime stage when applicable.

Configure a shared store once per WSL user with `pnpm config set --global storeDir "$HOME/.local/share/pnpm/store"`. Run `pnpm store path` in each checkout to verify they share the store.

Update the starter workflow, project pins, and Docker images together when changing the approved toolchain.
