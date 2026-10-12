# agent

An autonomous Linux agent, as a chat or a loop.

## Install

```bash
ovc pkg install agent
```

## Use as a chat

```bash
ovc agent
```

The first run asks for the endpoint once and stores it in
`~/.ovyth/agent.json`; after that you just type. No environment variables, no
goal to phrase in advance.

The model has four tools — a shell command, reading a file, writing a file, and
saying something back — and may take as many as it needs before answering, so
one line from you can be three commands on the machine.

Slash commands: `:help`, `:config key|url|model <value>`, `:readonly on|off`,
`:tools`, `:reset`, `:clear`, `:quit`.

## Use as a loop

```ov
import "agent"
import "agent/guard"

// ... your own loop: ask, run a guarded command, observe, repeat
```

`examples/agent/agent.ov` in the Ovyth repository is a worked example of the
batch form.

## The guard

A guard, not a lockdown. Writing, installing, cloning and building are the
point of an agent, so the question is not "does this change anything" but "does
this destroy something that cannot be built again" — the system roots, block
devices, and the machine's power state. Everything else is allowed.

`AGENT_PROTECT=path:path` adds paths; `AGENT_UNSAFE=1` disables it.

## Compatibility

Ovyth 0.1.4 or newer: it uses `os.run` and `os.tty`.

## License

MIT
