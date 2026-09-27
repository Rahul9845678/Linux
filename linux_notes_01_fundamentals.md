# Linux Interview Roadmap --- Notes

## How to use these notes

The goal is not to memorize commands. Build a mental model first, then
attach commands to that model.

------------------------------------------------------------------------

# 1. What is Linux?

## Mental model

Think of a Linux computer like a company:

-   **Kernel** = the manager who controls the actual resources.
-   **Shell** = the receptionist/interpreter through which you give
    instructions.
-   **Applications** = employees doing specific jobs.
-   **Hardware** = the physical office/resources.

The important idea:

> You normally do not talk directly to hardware. Applications request
> things from the kernel, and the kernel controls the hardware.

### Simple flow

``` text
You
 ↓
Shell
 ↓
Linux Kernel
 ↓
Hardware
```

Example:

When you run:

``` bash
ls
```

you are asking the shell to execute the `ls` program. The program asks
the operating system for information about the directory, and Linux
provides it.

------------------------------------------------------------------------

# 2. Kernel vs Shell

## Kernel

The **kernel is the core of the operating system**.

It manages:

-   CPU
-   Memory
-   Processes
-   Filesystems
-   Devices
-   Networking
-   Security/permissions

Mental model:

> Kernel = resource manager.

You don't normally interact with the kernel by typing commands directly.

## Shell

A **shell is a command interpreter**.

It takes what you type and starts programs/commands.

Examples:

-   Bash
-   Zsh
-   Fish

Mental model:

> Shell = translator between you and the operating system.

Example:

``` bash
pwd
```

You type the command into the shell. The shell executes the `pwd`
program, which asks the operating system for the current working
directory.

### Interview question

**Q: What is the difference between Linux kernel and shell?**

Answer:

> The kernel is the core component that manages system resources such as
> CPU, memory, processes and devices. The shell is a command interpreter
> that allows users to interact with the operating system.

------------------------------------------------------------------------

# 3. Linux Distribution

Linux itself refers primarily to the kernel. A **Linux distribution**
combines the Linux kernel with system tools, libraries, package managers
and applications.

Examples:

-   Ubuntu
-   Debian
-   Red Hat Enterprise Linux (RHEL)
-   Fedora
-   Rocky Linux
-   AlmaLinux

Mental model:

> Kernel = engine\
> Distribution = complete vehicle built around that engine.

Different distributions may use different package managers and have
different defaults, but the underlying Linux concepts remain largely the
same.

### Common package managers

Debian/Ubuntu:

``` bash
apt
```

RHEL/Fedora-family:

``` bash
dnf
yum
```

------------------------------------------------------------------------

# 4. Linux Filesystem --- The Most Important Mental Model

Linux has **one hierarchical filesystem tree**.

Start at:

``` text
/
```

This is called the **root directory**.

Do not confuse:

``` text
/
```

with:

``` text
/root
```

`/` is the top of the entire filesystem.

`/root` is the home directory of the root user.

## Mental model

Think of `/` as the main building.

Everything is located somewhere inside that building.

``` text
/
├── home
├── etc
├── var
├── tmp
├── opt
├── usr
├── dev
└── root
```

------------------------------------------------------------------------

# 5. Important Linux Directories

## `/home`

Normal users generally have their personal directories here.

Example:

``` text
/home/rahul
```

Mental model:

> `/home` = users' personal rooms.

------------------------------------------------------------------------

## `/root`

Home directory of the root user.

``` text
/root
```

Mental model:

> `/root` = administrator's personal room.

------------------------------------------------------------------------

## `/etc`

Contains system and application configuration files.

Examples may include:

``` text
/etc/hosts
/etc/passwd
/etc/ssh/
/etc/systemd/
```

Mental model:

> `/etc` = configuration cupboard.

When an application behaves incorrectly because of configuration, `/etc`
is often worth checking.

------------------------------------------------------------------------

## `/var`

Contains data that changes frequently.

Examples:

``` text
/var/log
/var/cache
/var/lib
```

Mental model:

> `/var` = constantly changing operational data.

------------------------------------------------------------------------

## `/var/log`

Contains logs.

Mental model:

> `/var/log` = system/application diary.

For production support, this directory is extremely important.

------------------------------------------------------------------------

## `/tmp`

Temporary files.

Mental model:

> `/tmp` = temporary workspace.

Do not assume files here are permanent.

------------------------------------------------------------------------

## `/opt`

Often used for optional or third-party software.

For example, an organization might install an application under:

``` text
/opt/myapp
```

Mental model:

> `/opt` = place for additional software.

------------------------------------------------------------------------

## `/usr`

Contains many user-space programs, libraries and shared resources.

You will commonly encounter:

``` text
/usr/bin
/usr/sbin
/usr/lib
```

For interview purposes, understand the purpose rather than memorizing
every subdirectory.

------------------------------------------------------------------------

## `/bin`

Contains essential user commands on systems where this directory is
separate.

Examples include commands such as:

``` text
ls
cp
mv
cat
```

Modern Linux distributions may merge `/bin` with `/usr/bin`, so don't
assume they are always physically separate.

------------------------------------------------------------------------

## `/dev`

Contains interfaces representing devices.

Examples:

``` text
/dev/sda
/dev/null
```

Mental model:

> `/dev` = doorway through which software interacts with devices/special
> device interfaces.

------------------------------------------------------------------------

## `/proc`

A virtual filesystem exposing information about running processes and
kernel/system state.

Example:

``` text
/proc/cpuinfo
/proc/meminfo
```

Mental model:

> `/proc` = live information window into the running system.

It is not a normal disk directory containing ordinary files.

------------------------------------------------------------------------

# 6. Absolute vs Relative Paths

## Absolute path

Starts from `/`.

Example:

``` bash
/home/rahul/project/app.log
```

It tells Linux exactly where to start.

Mental model:

> Absolute path = complete postal address.

------------------------------------------------------------------------

## Relative path

Starts from your current directory.

Example:

``` bash
project/app.log
```

If you are currently in:

``` text
/home/rahul
```

then Linux interprets it as:

``` text
/home/rahul/project/app.log
```

Mental model:

> Relative path = directions from where you are standing.

------------------------------------------------------------------------

# 7. `pwd` --- Where Am I?

Command:

``` bash
pwd
```

Meaning:

> Print Working Directory.

Example:

``` bash
$ pwd
/home/rahul
```

Mental model:

> `pwd` = GPS showing your current location.

------------------------------------------------------------------------

# 8. `ls` --- What Is Here?

Command:

``` bash
ls
```

Shows files/directories in the current directory.

Useful variations:

``` bash
ls -l
ls -a
ls -la
```

Mental model:

> `ls` = look around the room.

### `ls -l`

Shows detailed information.

### `ls -a`

Shows hidden files too.

### `ls -la`

Combines both.

------------------------------------------------------------------------

# 9. `cd` --- Move Around

Command:

``` bash
cd /var/log
```

Changes your current directory.

Useful shortcuts:

``` bash
cd ..
cd ~
cd -
```

Mental model:

> `cd` = move to another room.

-   `..` = parent directory
-   `~` = your home directory
-   `-` = previous directory

------------------------------------------------------------------------

# 10. First Mental Map

Remember Linux navigation like this:

``` text
                 /
                 |
       ---------------------
       |    |    |    |    |
     home  etc  var  tmp  opt
            |    |
          config logs
```

And remember:

``` text
pwd = Where am I?
ls  = What is here?
cd  = Move somewhere
```

These three commands form the foundation of Linux navigation.

------------------------------------------------------------------------

# Interview Checkpoint

Try answering these without looking:

1.  What is Linux?
2.  What does the kernel do?
3.  What is a shell?
4.  What is the difference between kernel and shell?
5.  What is a Linux distribution?
6.  What is `/`?
7.  Difference between `/` and `/root`?
8.  What is `/etc` used for?
9.  What is `/var/log`?
10. What is `/tmp`?
11. Difference between absolute and relative paths?
12. What does `pwd` do?
13. What does `ls -la` do?
14. What does `cd ..` do?
15. Why is `/proc` different from a normal directory?

## One-line memory trick

``` text
Kernel = controls
Shell = translates
/ = entire filesystem
/home = users
/etc = configuration
/var = changing data
/var/log = logs
/tmp = temporary
/opt = extra software
/dev = devices
/proc = live system information

pwd = where am I?
ls  = what's here?
cd  = move
```
