# Manus Streamer

This is a modified copy of `SDKClient_Linux` from the [MANUS Core SDK v2.4.0.1](https://docs.manus-meta.com/latest/Plugins/SDK/Windows/SDK%20Client/). It connects to a MANUS Core instance and streams hand skeleton data over ZMQ (push sockets).

Each hand publishes on its own channel:

| Channel | Port | Description |
|---------|------|-------------|
| Left hand skeleton | `tcp://*:8002` | Per-frame joint data for the left hand |
| Right hand skeleton | `tcp://*:8003` | Per-frame joint data for the right hand |
| Full skeleton | `tcp://*:8000` | Combined skeleton (all joints) |
| Ergonomics | `tcp://*:8001` | Ergonomics data for connected gloves |

---

# Usage

## Dependencies

Install the required system libraries:

```bash
sudo apt install libzmq3-dev libncurses5-dev
```

## Build

```bash
make
```

This produces `SDKClient_Linux.out` in the same directory.

## Run

```bash
sudo ./SDKClient_Linux.out
```

On startup, select the connection type:
- **[1] Core Integrated** — runs standalone, no MANUS Core instance needed
- **[2] Core Local** — connects to a MANUS Core running on the same machine

Once connected, the application begins streaming hand data over the ZMQ ports listed above.
