GLOSSARY.md: Project Terminology

This document defines key terms used throughout the OpenDrive project's source code, documentation, and issue tracker.
A

    API (Application Programming Interface)

        Refers to the Google Drive API, the set of rules and protocols that OpenDrive uses to communicate with Google's servers to manage files.

    Authentication

        The process of securely verifying a user's identity with Google. OpenDrive uses the OAuth 2.0 protocol for this.

C

    CLI (Command-Line Interface)

        The text-based interface for interacting with the OpenDrive daemon from a terminal. Contrasts with the GUI.

    Conflict (Sync Conflict)

        A state that occurs when a file is modified in two different locations (locally and on Google Drive) before the changes can be synchronized. OpenDrive must have a strategy to resolve these conflicts.

    Crate

        A Rust package or library. The term is used to refer to third-party dependencies used in the project.

D

    Daemon

        A long-running background process that contains the core logic of the application. The OpenDrive daemon runs without a visible window and manages all synchronization tasks.

    D-Bus

        A message bus system, the standard for Inter-Process Communication (IPC) on modern Linux desktops. OpenDrive uses it for the GUI and CLI to communicate with the Daemon.

F

    FUSE (Filesystem in Userspace)

        A system that allows non-privileged users to create their own filesystems without editing kernel code. OpenDrive plans to use FUSE to implement On-Demand Sync, where remote files are shown as local placeholders.

G

    GUI (Graphical User Interface)

        The visual, window-based application that allows users to configure settings, check status, and manage their account. It is separate from the Daemon.

I

    IPC (Inter-Process Communication)

        The mechanism used for different processes to communicate with each other. In OpenDrive, this refers to the GUI and CLI talking to the Daemon via D-Bus.

M

    Metadata

        Data about files, not the content of the files themselves. This includes file names, modification dates, version identifiers (etags), and Google Drive file IDs. This information is stored in the local SQLite database.

O

    OAuth 2.0

        An open standard for access delegation, commonly used as a way for users to grant websites or applications access to their information on other websites but without giving them the passwords. This is the only way OpenDrive will access user accounts.

    On-Demand Sync (Smart Sync)

        A feature where files from Google Drive are visible on the local filesystem as placeholders but are only downloaded when the user tries to open them. This saves significant local disk space.

S

    Selective Sync

        A feature that allows users to select only specific folders from their Google Drive to download and synchronize, rather than their entire Drive.

    Shared Drive (formerly Team Drive)

        A special Google Drive folder structure for teams, with different ownership and permission models than a user's personal "My Drive" space.

    Sync Engine

        The core component of the Daemon responsible for comparing local and remote files, detecting changes, and executing the necessary operations (upload, download, delete, rename) to keep them consistent.