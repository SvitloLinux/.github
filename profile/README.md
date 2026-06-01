# Svitlo GNU/Linux

> Independent GNU/Linux distribution from Ukraine with its own package base

### Support the project

[![BuyMeACoffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/kachanyk)
[![Patreon](https://img.shields.io/badge/Patreon-F96854?style=for-the-badge&logo=patreon&logoColor=white)](https://www.patreon.com/SvitloLinux)

## What it is

Svitlo is a minimal graphical GNU/Linux system built entirely from source by a single engine called promin. The whole userspace, from the toolchain (binutils, gcc, glibc), kernel, bootloader and base utilities, through graphics, network and wifi, up to applications, is compiled from source through declarative recipes

The bootable image is a composition of prebuilt store packages (a profile generation), not a separate install phase. The image carries the kernel, the bootloader, the network and wifi stack, and promin itself so the system can manage itself. Graphical layer is Wayland with the Sway compositor

Every binary is traceable to its source, version and dependency set through a single hash. The system is Svitlo, the package manager is promin

## Package manager (Nix model)

promin follows the Nix model. Each package is installed into a path keyed by a hash of all build inputs

```
/promin/store/<hash>-<name>-<version>/
```

The hash is computed from the source, version, recipe body and the hashes of all dependencies. Different versions or flags produce different paths, so multiple versions coexist without conflict. The active environment is a symlink farm (a profile generation), switching between generations is atomic and rollback is instant

The hash is computed from a canonical representation of the recipe, not from its raw text, so cosmetic edits do not trigger needless rebuilds

## Client and server

promin is client-server. A thin server distributes recipes, sources and binary packages keyed by hash over HTTP. The server does not build anything itself. On an installed system promin acts as a client and install is binary-first

```
in store?  ->  local cache?  ->  binary from server (hash match)?  ->  build from source
```

A prebuilt binary is verified by sha256 before unpacking. For the end user this means packages download ready-made as in any ordinary distribution, while building from source stays an infrastructure detail on the server side

## For whom this distribution is planned

Educational institutions, schools and universities. An open-licensed OS with a bundled software set. Reproducibility means the lab environment is identical down to the bit across all machines, and a broken machine is restored in seconds by rolling back a generation

State and public sector. The argument is auditability of the supply chain, every binary traceable to its source through a hash with no opaque third-party blobs, full logging of user actions, and data encryption. Relevant certificates and licenses are planned

Computer and laptop vendors. An OS for pre-sale installation, with simple setup and tools to demonstrate processor and graphics characteristics

Individuals who value simplicity and reliability with strong protection and privacy

## Philosophy

Svitlo aims to be simple, clear, logical, open and secure

- Simple and clear interface
- Obvious and useful software set
- Data encryption with a unique key generated at install time (planned)
- No tracking and no transmission of analytics from the browser or any installed software (planned)
- A system usable immediately after install, with a powerful yet simple package manager to tailor software to the user

## Design principles

Built from source, fully reproducible, transparent from source to binary. Minimalism over feature creep. The user owns the whole stack

## Status and scope

Target hardware is x86_64, which covers the bulk of desktops and laptops. ARM support is planned as the next step. Graphics in the current shape is Wayland with Sway. The system uses glibc

## Roadmap

In development

## Documentation

In development

> Copyright (C) 2025 Yurii Kachaniuk, Ukraine <wku@ukr.net>

[![Telegram](https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/SvitloLinux)
