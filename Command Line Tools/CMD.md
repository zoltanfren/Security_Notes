# Summary

## Windows Command Execution Path
- Commands can only run if they exist in directories listed in the **PATH environment variable**.
- The `set` command shows environment variables including `Path`.
- The **Path variable** lists directories where Windows searches for executables.

Example:
Path=C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;...

## Checking the Windows Version
- The `ver` command displays the **Windows OS version**.

Example output:
Microsoft Windows [Version 10.0.17763.1821]

## Getting System Information
- The `systeminfo` command shows detailed system information:
  - Host name
  - OS name and version
  - OS manufacturer
  - System configuration
  - Processor and memory details

## Handling Long Output
- Use `| more` to display long outputs page by page.

Example:
driverquery | more

Navigation:
- Spacebar → next page
- CTRL + C → exit

## Useful Commands
- `help` → shows help for commands
- `cls` → clears the Command Prompt screen