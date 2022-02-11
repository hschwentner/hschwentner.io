# hschwentner.io

Henning Schwentner's personal website

## Development

### Setup environment

Install Docker Desktop:

```fish
brew install --cask docker
```

### Day-to-day Development

To run a server locally:

```fish
docker compose up
```

## Development without Docker

### Setup environment

Install Ruby and Jekyll

```fish
brew install rbenv
rbenv install 2.7.3
gem install bundler jekyll
bundle install
```

### Day-to-day Development

To run a server locally:

```fish
bundle exec jekyll serve
```

Occasionally run:

```fish
bundle update
```
