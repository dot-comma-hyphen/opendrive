TODO.md: Implementation Plan & Checklist

This document tracks the major tasks required to build and maintain the OpenDrive application and its documentation ecosystem. It is a living document that will be updated as the project progresses.
Phase 1: Core Functionality (MVP)

This phase focuses on delivering a Minimum Viable Product that fulfills the core promise of the application: reliable, two-way synchronization.
1.1. Project Foundation

    [x] Create initial project file structure (README.md, VISION.md, GLOSSARY.md, TODO.md).

    [ ] Set up Git repository and CONTRIBUTING.md guidelines.

    [ ] Choose and implement a logging strategy (env_logger, tracing).

    [ ] Set up basic CI/CD pipeline for automated builds and testing on GitHub Actions.

1.2. Core Sync Daemon

    [ ] Authentication:

        [ ] Implement the OAuth 2.0 flow to securely obtain user credentials.

        [ ] Implement secure storage for refresh tokens (using secret-service crate).

    [ ] API Client:

        [ ] Create a robust client for interacting with the Google Drive v3 API.

        [ ] Implement files.list for initial file discovery.

        [ ] Implement file download and upload functionality.

        [ ] Implement file delete, rename, and move operations.

    [ ] Metadata Database:

        [ ] Design the SQLite database schema (file mappings, versions, etc.).

        [ ] Implement rusqlite logic for database creation and access.

    [ ] Initial Sync Logic:

        [ ] Implement the logic to fetch the remote file tree and populate the database.

        [ ] Implement the logic to download all files for a "full sync" setup.

    [ ] Continuous Sync Logic:

        [ ] Implement a file system watcher using the notify crate to detect local changes.

        [ ] Implement handling for local create, modify, and delete events.

        [ ] Set up Google Drive Push Notifications to receive remote changes.

        [ ] Implement logic to process remote changes from the changes.list API.

    [ ] Conflict Resolution:

        [ ] Implement the basic conflict resolution strategy (rename local file as "conflicted copy").

1.3. User Interfaces (IPC & Frontends)

    [ ] IPC Layer:

        [ ] Define the D-Bus service interface (.xml file).

        [ ] Implement the D-Bus server in the daemon using zbus.

        [ ] Implement D-Bus clients for the GUI and CLI.

    [ ] GUI (MVP):

        [ ] Create an initial setup wizard for authentication and folder selection.

        [ ] Create a basic settings window to show account info and sync status.

        [ ] Implement a system tray icon with status indicators (Synced, Syncing, Paused, Error).

        [ ] Implement selective sync folder tree view.

    [ ] File Manager Integration:

        [ ] Create a script/instructions for adding a "View on Google Drive" context menu item.

Phase 2: Advanced Features (Post-1.0)

This phase focuses on building features that enhance the user experience and cater to power users.

    [ ] On-Demand Sync (Smart Sync):

        [ ] Research and implement a FUSE driver using the fuser crate.

        [ ] Integrate the FUSE filesystem with the sync daemon.

    [ ] Advanced Sharing:

        [ ] Add "Share..." option to the file manager context menu.

        [ ] Build a GUI to manage permissions and generate shareable links.

    [ ] Command-Line Interface (CLI):

        [ ] Implement opendrive status command.

        [ ] Implement opendrive pause and opendrive resume commands.

        [ ] Implement commands for managing selective sync from the terminal.

    [ ] Multi-Account Support:

        [ ] Refactor auth and daemon logic to handle multiple user profiles.

        [ ] Add an account switcher to the GUI.

    [ ] Shared Drives Support:

        [ ] Extend the API client and sync logic to handle Shared Drives.

Phase 3: Distribution & Maintenance

    [ ] Packaging:

        [ ] Create a Flatpak manifest and publish on Flathub.

        [ ] Create a Snapcraft configuration and publish on the Snap Store.

        [ ] Set up a build process for .deb and .rpm packages.

    [ ] Documentation:

        [ ] Write comprehensive user guides for installation and usage.

        [ ] Create detailed developer documentation for contributors.

        [ ] Set up a project website or documentation site.