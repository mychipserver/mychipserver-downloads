# mychipserver downloads

Official downloads for [mychipserver.com](https://mychipserver.com): use real
microcontroller boards remotely, with your own debugger.

## mychipserver desktop app (Windows)

**[Download mychipserver.msi](https://github.com/mychipserver/mychipserver-downloads/raw/main/mychipserver.msi)**: version 3.2.0

1. Install it and start mychipserver.
2. It opens mychipserver.com in your browser: click **Link** (once per PC).
3. Every board you reserve then gets a local debug port on this PC:

   ```
   arm-none-eabi-gdb firmware.elf -ex "target remote 127.0.0.1:3333"
   ```

Works with GDB, VS Code (Cortex-Debug), CLion and any tool that connects to a
GDB server. Several boards get 3333, 3334, … in a stable order.

## mcsrack command-line tool

The same connection as a single program, for Linux, macOS, Windows and CI:

| System | Download |
|---|---|
| Windows (x64) | [chipserver-bridge-win.exe](https://github.com/mychipserver/mychipserver-downloads/raw/main/chipserver-bridge-win.exe) |
| Linux (x64) | [chipserver-bridge-linux](https://github.com/mychipserver/mychipserver-downloads/raw/main/chipserver-bridge-linux) |
| macOS (Intel; runs on Apple silicon with Rosetta) | [chipserver-bridge-macos](https://github.com/mychipserver/mychipserver-downloads/raw/main/chipserver-bridge-macos) |

Version 0.1.0. Check yours with `--version`.

On your board's page on mychipserver.com, copy the connect command and run it
with the program you downloaded:

```
./chipserver-bridge-linux debug --wss <address from mychipserver.com>
```

- **Linux and macOS:** make it executable first: `chmod +x chipserver-bridge-*`.
- **macOS:** the first run is blocked because the program is not yet signed.
  Allow it in **System Settings → Privacy & Security**, or run
  `xattr -d com.apple.quarantine chipserver-bridge-macos`.
- **Windows:** SmartScreen may warn about an unrecognised app. Choose **More
  info → Run anyway**.

`--help` lists every command.

## Checking a download

`SHA256SUMS` lists the checksum of every file:

```
sha256sum -c SHA256SUMS                                  # Linux
shasum -a 256 -c SHA256SUMS                              # macOS
Get-FileHash .\mychipserver.msi -Algorithm SHA256        # Windows PowerShell
```

## Help

- Getting started and documentation: https://mychipserver.com
- Support: support@mychipserver.com

Copyright © MyChipServer. All rights reserved.
