# RPM

## RPM General
- for the Red Hat family of Linux: Fedora, CentOS, RHEL, **Tizen**
- a file containing other files and information about them needed by the system
- consists of: cpio archive (containing files) and RPM header
- RPM header used to determine dependencies, location of installation, etc.
- Two RPM types: source RPM (SRPM) and binary RPM.

An SRPM contains source code, optionally patches, and a SPEC file describing how to build the source code and patches.

## SPEC file
A *recipe* that the `rpmbuild` utility uses to actually build an RPM.
Instructions are defined in a series of sections; sections are defined in the *Preamble* and the *Body*.
The *preamble* contains a series of metadata items that are used in the *Body*. The *Body* contains the main part of the instructions.

### Body Items
| SPEC directive | Definition |
|---|---|
| %description | A full description of the software packaged in the RPM. |
| %prep | Command or series of commands to prepare the software to be built, for example, unpacking the archive in  Source0. |
| %build | Command or series of commands for actually building the software into  machine code (for compiled languages) or byte code (for some interpreted  languages). |
| %install | Command or series of commands for copying the desired build artifacts from the  %builddir (where the build happens) to the  %buildroot directory (which contains the directory structure with the files to be packaged). This usually means copying files from  ~/rpmbuild/BUILD to ~/rpmbuild/BUILDROOT and creating the necessary directories in ~/rpmbuild/BUILDROOT. This is only run when creating a package, not when the end-user installs the package. |
| %check | Command or series of commands to test the software. This normally includes things such as unit tests. |
| %files | The list of files that will be installed in the end user’s system. |
| %changelog | A record of changes that have happened to the package between different Version or Release builds. |

### BuildRoots
In the context of RPM packaging, "buildroot" is a `chroot` environment. The build artifacts are placed here using the same filesystem hierarchy as will be in the end user's system, with "buildroot" acting as root directory. The placement of build artifacts should comply with the filesystem hierarchy standard of the end user's system.