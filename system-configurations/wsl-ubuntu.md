# WSL (Ubuntu 20) on Windows 10
_these instructions are for WSL 1_
* [Official Microsoft Documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

## Install WSL

Open a Powershell prompt and enter:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

## Install Linux Distribution
* [Official Microsoft Documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10#install-your-linux-distribution-of-choice)

Get the officially supported Ubuntu version from the Windows store: [Ubuntu 20.04 LTS](https://www.microsoft.com/store/apps/9n6svws3rx71)

__Once you have completed installation, you can then proceed to the development environment setup below.__

---

## Install/Verify NodeJS

## Install/Verify Git

## Install/Verify Ruby
_only required if developing with a Ruby-based language_
