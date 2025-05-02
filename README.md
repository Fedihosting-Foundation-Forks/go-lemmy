# Go-Lemmy

[![Go Reference](https://pkg.go.dev/badge/github.com/Fedihosting-Foundation-Forks/go-lemmy.svg)](https://pkg.go.dev/github.com/Fedihosting-Foundation-Forks/go-lemmy)

Go bindings to the [Lemmy](https://join-lemmy.org) API, automatically generated from Lemmy's source code using the generator in [cmd/gen](cmd/gen).

### Examples

Examples can be found in the [examples](examples) directory.

### How to generate

First, update the [lemmy-js-client](https://github.com/LemmyNet/lemmy-js-client) submodule :

```bash
git submodule update --init
```

For generating from another version, simply check out another version in the submodule folder.

Inside it, build the JSON docs file:

```bash
pnpm install
pnpm run docs --json ../docs.json
```

Back in the root folder, remove all the existing generated code:

```bash
find . -type f -name '*.gen.go' -print -delete
```

Execute the generator:

```bash
go run cmd/gen/main.go -json-file docs.json -out-dir .
```

And that's it! Your generated code should be ready for use.
