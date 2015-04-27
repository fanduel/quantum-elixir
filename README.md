# Quantum [![Hex.pm Version](http://img.shields.io/hexpm/v/quantum.svg)](https://hex.pm/packages/quantum)

[Cron](https://en.wikipedia.org/wiki/Cron)-like job scheduler for [Elixir](http://elixir-lang.org/) applications.

## Setup

To use Quantum in your projects, edit your mix.exs file and add Quantum as a dependency:

```elixir
defp deps do
  [
    { :quantum, ">= 1.0.0" }
  ]
end
```

Then, add Quantum to the list of applications in your `mix.exs' file:

```elixir
def application do
  [
    applications: [ :quantum ]
  ]
end
```

## Usage

Configure your cronjobs in your `config/config.exs` like this:

```elixir
config :quantum, cron: [
    "* * * * *": fn -> IO.puts("every minute") end,
    "*/2 * * * *": fn -> IO.puts("every two minutes") end,
    # Runs on 18, 20, 22, 0, 2, 4, 6:
    "0 18-6/2 * * *": fn -> IO.puts("it's late") end,
    # Runs every midnight:
    "@daily": &backup/0
]
```

## License

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)
