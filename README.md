# CESMIX

A Julia Package Registry for packages related to CESMIX.

To install open a Julia REPL and type
```{julia}
] registry add https://github.com/cesmix-mit/CESMIX.git
```
Afterwards use the normal package manager commands to add, remove, dev, etc the packages in this registry.

## Registering a Package or a new version

Both registering a new package or a new version uses
[`LocalRegistry`](https://github.com/GunnarFarneback/LocalRegistry.jl).
This needs to be installed first:
```julia
] add LocalRegistry
```

Suppose now that we want to register a new version of `JuLIP.jl`:
1. `] dev JuLIP`; we will assume this puts `JuLIP` into  `~/.julia/dev/JuLIP/`.
2. make the changes to the package
3. Bump the version number, by manually editing `Project.toml`, commit and push.
4. Now the following sequence of commands will register the new version in the `CESMIX` registry.
   ```julia
   using LocalRegistry
   using JuLIP
   register(JuLIP, "CESMIX")
   ```
   This edits the registry files and commits the changes.
   If the package has already been registered before (i.e. this is a version update),
   then a simple `register(<packagename>)` is sufficient.
5. Finally, we need to push the registry
   ```bash
   cd ~/.julia/registries/CESMIX
   git push
   ```
