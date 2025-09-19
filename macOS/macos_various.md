# macOS - related General Information

Note that I am not a regular macOS user (Mac mini w/Apple Silicon M1).

## Filesystem

[Source: Apple Developer](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html#//apple_ref/doc/uid/TP40010672-CH2-SW2)

APFS is the default filesystem in macOS, iOS, watchOS and tvOS, replacing HFS+ (*Hierarchical File System*) as default filesystem for:
- iOS 10.3 andd later,
- macOS High Sierra and later

### Filesystem Basics

iOS application interaction with the filesystem is limited only to its *sandbox directory*. During installation, installer creates a number of *container directories* within the app's sandbox directory.

- Application
    - Sandbox directory
        - Bundle Container
            - MyApp.app
        - Data Container
            - ...
        - iCloud Container (if requested...)

Application has no access to files outside its sandbox directory, apart from using public system interface to access i.e. contacts or music.

```AppName.app``` is an application's bundle. It contains the executable and related resources. Directory signed at installation time, any changes to its contents changes the signature and prevents the app from launching.

### Domains

macOS filesystem is divided into multiple domains.
- User domain
    - Resources specific for a user logged into the system. Technically encompasses all users, but at the runtime, this domain reflects only the home directory of the current user.
- Local domain
    - Resource specific for the computer, shared among all users, typically managed by the system, may be modified by admins.
- ...
- System domain
    - System software installed by Apple, required by the system to run, unavailable to user.

### macOS Standard Directories: Where Files Reside

| Name  | Desc | Domain |
| ------------- | ------------- | ------ |
| ```/Applications```  | Applications intended to be used by all the users of the computer  | Local |
| ```Library```  | Apps - specific resources  | Different domains / specific user |
| ```System``` | Resources provided by Apple; must not be modified | System |
| ```Users``` | One or more user home directories | User |

In terms of hidden files and directories, these include i.e.:
- UNIX - specific directories (inherited from traditional UNIX installations; important part of the system’s BSD layer).
- Packages and bundles (presented to user as if they were files).
- Dot files/directories, etc.

Names of the file/directories displayed don't have to match those visible in the filesystem; they are called *display names*.
Type of the contents of the file is identified via:
- Filename extension,
- UTIs (Uniform Type Identifiers).

### Filesystem - Security
- Sandboxing,
- Access Control Lists & BSD permissions mix,
- macOS / iOS supports file encryption via Disk Utility. macOS: decryption keys are destroyed when computer is turned off / put to sleep.