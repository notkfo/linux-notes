# Linux Filesystem Hierarchy Standard (FHS)

The Filesystem Hierarchy Standard (FHS) defines the directory structure and where to store directory contents in Unix-like operating systems. It is maintained by the Linux Foundation.

## Key Points to Keep in Mind

- All files and directories are stored under the root directory `/`. Even if they are stored on a virtual device or a different physical device.
- Don't expect every directory mentioned here to exist by default. If software that needs a certain directory is installed, that software's installer will create it.
- Most of the directories mentioned here exist in all UNIX operating systems and are used in the same way.

---

## Directory Reference

### 1. `/` — Root
The root directory sits at the top of the filesystem tree, represented by a forward slash `/`. Since it is the base point, there is no directory above it.

- All other directories branch from here.
- Modifying the contents of the root directory requires root permissions. Attempting to add files without root permission will result in a "Permission Denied" error.

---

### 2. `/bin` — User Commands
Contains essential commands and binaries needed by all users. Examples include `cp`, `ls`, `ssh`, `date`, and `sort`. These are the tools needed for basic daily system interaction.

- Contains **binary executables** — programs that have been compiled down to machine code, so the CPU can run them directly without a compilation step each time.

---

### 3. `/boot` — System Startup
Contains all files required for booting the system, including the bootable Linux kernel itself and boot loader configuration files. Without it, the system will not be able to boot.

---

### 4. `/dev` — Device Files
Contains device files that act as an interface between hardware and software. Device files have two types:

- **Block device:** Data is read/written in fixed-size chunks (blocks). Supports random access, meaning you can jump to any block directly. Hard drives and USB drives are classic examples.
- **Character device:** Data flows as a continuous stream, one character at a time, in order. No random access — you read it sequentially as it comes. Keyboards and mice are classic examples.

---

### 5. `/etc` — Configuration Central
Contains system configuration files. Most files here are in plain text, making them editable with any text editor (with proper permissions). From network settings to service configurations, if it controls how your system behaves, it is likely configured here.

- Also contains startup and shutdown scripts used to start/stop programs.

---

### 6. `/home` — User Directories
The personal space for each user. Here you will find Desktop, Documents, Downloads, Music, Pictures, and various personal project files. Each user can create, delete, and modify files stored in their own home directory. Accessing another user's home directory depends on the system's security configuration.

---

### 7. `/lib` — Shared Libraries
Stores libraries that programs need to function at runtime. Programs share the same copies of a needed library to avoid duplication and save space. The essential commands in `/bin` and `/sbin` depend on it during system boot.

---

### 8. `/media` — Removable Media
Removable devices like USBs, CDs, and external drives are mounted here automatically by the OS when plugged in. For example, a USB drive typically appears at `/media/username/usb`.

- Acts as a temporary mount point for removable devices.

---

### 9. `/mnt` — Temporary Mount Point
Used for temporary manual mounts performed by the system administrator. For example, temporarily attaching a network drive or another disk is done by mounting it under `/mnt` manually.

- Unlike `/media`, the mount here is done manually and temporarily, usually by an admin for a specific task.

---

### 10. `/opt` — Optional Software
Contains third-party software and packages that are not part of the default system installation, along with their configuration and data files.

- Contains add-on applications from individual vendors.

---

### 11. `/sbin` — System Administration
Contains administrative commands and daemon processes. Commands here require root privileges to execute and are used for system maintenance and configuration.

- Like `/bin`, it also contains binary executables.

---

### 12. `/srv` — Service Data
Stores data that is served out by services running on the system. For example, if the machine is running a web server, the website files would be stored here.

---

### 13. `/tmp` — Temporary Files
Temporary files created by programs during execution are stored here. Files stored in `/tmp` are typically deleted on system reboot.

---

### 14. `/usr` — Unix System Resources
Contains a large collection of programs, libraries, documentation, and data files that are **not needed during the initial boot process** but are used once the system is fully up and running. The bulk of your installed software lives here.

- `/usr/bin` — Programs available to all users (e.g. `python`, `git`, `vim`)
- `/usr/lib` — Libraries for those programs
- `/usr/share` — Shared data such as documentation and icons

The key distinction from `/bin` and `/lib`: those directories contain only what is needed to boot the system and perform basic recovery. `/usr` contains everything else.

---

### 15. `/proc` — Process Information
Not actually stored on disk — generated dynamically by the kernel. Provides information about system resources, running processes, and hardware. Each running process is assigned a unique ID and represented as a directory inside `/proc`.
