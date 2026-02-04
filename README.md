# Notes to Self

## Install `containerlab`
```bash
# See https://containerlab.dev/install/
curl -sL https://containerlab.dev/setup | sudo -E bash -s "all"
```

## Checksum and then Import a cEOS image into the containerlab host
```bash
sha512sum -c cEOS-lab-4.35.0F.tar.sha512sum && \
docker import cEOS-lab-4.35.0F.tar.xz ceos:4.35.0F
```

## Start cLab
```bash
sudo containerlab deploy --topo single-dc-l3ls/l3lsexample.clab.yml
```

## Install `uv`
```bash
# On macOS and Linux.
curl -LsSf https://astral.sh/uv/install.sh | sh
# On Windows.
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

## Run Build Playbook in `uv`.
```bash
# From the repo root folder
uv sync --upgrade && \
uv run ansible-galaxy collection install -r requirements.yaml && \
uv run ansible-playbook single-dc-l3ls/build.yml -i single-dc-l3ls/inventory.yml --check --diff
```

## Update the `uv` manager
```bash
uv self update
```