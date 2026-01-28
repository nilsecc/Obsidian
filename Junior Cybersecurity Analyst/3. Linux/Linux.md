
# Introduction

**Linux Structure**  
Linux is an open-source operating system used on desktops, servers, embedded systems, and mobile devices. It is a core platform in cybersecurity due to stability, security, and flexibility. Exists in many distributions (distros) tailored to different needs.

**History**  
Linux originates from Unix (1970). GNU project (1983) aimed to create a free Unix-like OS. Linux kernel was created in 1991 by Linus Torvalds. Licensed under GPLv2. Today it has millions of lines of code and hundreds of distributions (Ubuntu, Debian, Fedora, Mint, etc.).

**Why Linux is Important**  
More secure and stable than many OSs, less malware-prone, frequently updated. Open-source allows modification and redistribution. Used everywhere: servers, desktops, embedded systems, Android.

**Linux Distributions**  
Different versions of Linux built on the same kernel. Examples: Ubuntu, Debian, Fedora, Arch, Linux Mint, Parrot OS. Parrot OS is security-focused and used for pentesting.

**Linux Philosophy**  
Based on simplicity, modularity, and openness. Uses small tools that do one thing well and can be combined. Configuration stored in text files and heavy use of the terminal.

**Core Principles**  
- Everything is a file.  
- Small single-purpose programs.  
- Programs can be chained together.  
- Avoid captive user interfaces (CLI preferred).  
- Configuration stored in text files (e.g. /etc/passwd).

**Main Components**  
- Bootloader: starts the OS (e.g. GRUB).  
- Kernel: manages hardware and system resources.  
- Daemons: background services.  
- Shell: command-line interface (Bash, Zsh, etc.).  
- Graphics Server: provides graphical support (X server).  
- Window Manager / GUI: graphical interface (GNOME, KDE, etc.).  
- Utilities: tools and applications.

**Linux Architecture**  
- Hardware: physical components.  
- Kernel: controls and virtualizes hardware resources.  
- Shell: interface between user and kernel.  
- System Utilities: provide OS functionality.

**File System Hierarchy**  
Linux uses a tree-like structure defined by the FHS standard.
![[Pasted image 20260128173404.png]]

**Root Directory (/)**  
Top-level directory containing everything required to boot and run the system.

**Important Directories**  
`/bin`: essential system commands.  
`/boot`: bootloader and kernel files.  
`/dev`: device files.  
`/etc`: system and application configuration.  
`/home`: user directories.  
`/lib`: essential shared libraries.  
`/media`: removable media mount points.  
`/mnt`: temporary mounts.  
`/opt`: optional and third-party software.  
`/root`: root user home directory.  
`/sbin`: system administration binaries.  
`/tmp`: temporary files.  
`/usr`: user programs, libraries, documentation.  
`/var`: variable data (logs, mail, web data).

# Shell

**Introduction to Shell**  
Learning the Linux shell is essential because many servers run Linux, especially web servers. The shell allows full control of the operating system and is more powerful than using only the GUI.

**Terminal / Shell / Console**  
A terminal (or shell, command line) is a text-based interface between the user and the kernel. It allows executing commands to control the system. The term console refers to a text-mode screen, not a window.

**Purpose of the Shell**  
Acts as a text-based interface to perform tasks like navigating directories, managing files, executing programs, and retrieving system information, with more flexibility and power than a GUI.

**Terminal Emulators**  
Software that emulates a terminal inside a graphical environment (GUI). They allow users to interact with the shell using text-based commands within a window.

**Command-Line Interfaces (CLI)**  
CLIs can run multiple terminals within one terminal session. They allow parallel command execution and multitasking.

**Terminal Multiplexers**  
Tools that extend terminal functionality by allowing multiple panes, sessions, and workspaces in a single terminal window. Example: tmux.

**Shell**  
The shell interprets user commands and communicates with the kernel. Everything done via GUI can also be done via the shell, often faster and more efficiently.

**Bash (Bourne-Again Shell)**  
The most commonly used Linux shell. Part of the GNU project. Supports scripting and automation, making repetitive tasks easier.

**Other Shells**  
Alternative shells include Tcsh/Csh, Ksh, Zsh, and Fish, each with different features and user experience.

![[Pasted image 20260128175448.png]]

