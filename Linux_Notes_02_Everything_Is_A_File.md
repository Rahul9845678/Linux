# Linux Notes 02 — Everything Is a File

## Concept

One of the most useful Linux mental models is:

> Linux represents many things through the filesystem.

This does not mean every object is literally an ordinary file. It means the filesystem is a central interface through which Linux represents and exposes many resources.

## Mental Model

Think of Linux as a huge office building:

```text
/
├── home/     → users' workspaces
├── etc/      → configuration
├── var/      → changing operational data
├── dev/      → device interfaces
├── proc/     → live process/system information
└── tmp/      → temporary workspace
```

Instead of thinking "Where is the setting?", think:

> "Which file or filesystem location represents this information?"

## Examples

### Normal file

```text
/home/rahul/notes.txt
```

Contains ordinary data.

### Configuration

```text
/etc/hosts
```

Contains host-name mappings.

### Logs

```text
/var/log/
```

Contains system/application logs.

### Device interface

```text
/dev/null
```

A special device interface commonly used to discard output.

### Process/system information

```text
/proc/cpuinfo
/proc/meminfo
```

These expose information about the currently running system.

## Important distinction

Not everything under Linux is a normal disk file.

Linux has different kinds of filesystem objects, including:

- Regular files
- Directories
- Symbolic links
- Device files
- Other special filesystem objects

Interview-safe statement:

> Linux uses a unified filesystem interface to represent and access many different types of resources.

## Why this matters in production support

When an application is failing, you may investigate:

```text
/etc/      → configuration
/var/log/  → logs
/proc/     → system/process information
/dev/      → device interfaces
```

This mental model helps you know where to look during troubleshooting.

## Interview Questions

### Q1. What does "everything is a file" mean in Linux?

> Linux uses a filesystem-based interface to represent and access many resources, including regular files, directories, devices and system information. However, not everything is literally an ordinary file.

### Q2. Is everything literally a regular file?

No. Linux has regular files, directories, symbolic links and special filesystem objects such as device interfaces.

### Q3. Why is this concept useful?

It provides a consistent way to interact with many system resources and makes Linux inspection and troubleshooting easier.

## Memory Trick

```text
/etc  → configuration
/var  → changing data
/var/log → records/logs
/dev  → devices
/proc → live system information
```

Think:

> Linux exposes much of the system through filesystem paths.

## Practice

Without looking back, explain:

1. What does "everything is a file" mean?
2. Is everything literally a regular file?
3. What would you look under `/var/log` for?
4. What kind of information can `/proc` expose?
5. Why is `/dev` special?
