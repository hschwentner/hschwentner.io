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

Or to rebuild the Docker image:

```fish
docker compose up --build
```

## Development without Docker

### Setup environment

Install Ruby and Jekyll

```fish
brew install rbenv
rbenv install
gem install bundler
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
