# leroyshirto.github.io

Personal portfolio and blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.157.0 or later)
- Git

## Getting Started

Clone the repo with submodules:

```bash
git clone --recurse-submodules https://github.com/leroyshirto/leroyshirto.github.io.git
cd leroyshirto.github.io
```

If you already cloned without `--recurse-submodules`, fetch the theme with:

```bash
git submodule update --init --recursive
```

## Local Development

Start the dev server:

```bash
hugo server -D
```

The site will be available at [http://localhost:1313](http://localhost:1313). The `-D` flag includes draft posts. The server live-reloads on file changes.

## Creating a New Post

```bash
hugo new posts/my-new-post.md
```

## Building for Production

```bash
hugo --gc --minify
```

Output goes to the `public/` directory.

## Deployment

Pushes to `main` automatically deploy to GitHub Pages via the workflow in `.github/workflows/hugo.yml`.
