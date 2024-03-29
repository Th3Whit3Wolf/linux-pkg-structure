# Glossary

## Basic Definitions

### Hardware

A computer’s **hardware** comprises the physical components of the computer, like its **hard drive** (or **hard disk drive** [**HDD**]) on which information is stored (analogous to a person’s long-term memory), **random-access memory** (**RAM**) devices (analogous to someone’s working memory) and **central processing unit** (**CPU**) or processor (which is where information processing is done, this processing is analogous to a person’s thoughts). The term “computer architecture” or “**instruction set architecture**” (**ISA**) refers to the set of instructions that the CPU, in question, can understand.

### Software

A computer’s software are the non-physical components to the computer, which are stored in the computer’s hard drive. It includes the data stored on the hard drive like one’s files as well as the computer programs, which are more or less just instructions for the computer’s processor. For example, as I am writing this post I am using the Atom text editor, which is a computer program.

### Source Code

**Source code** is a collection of computer instructions written in at least one human-readable computer language. The type of computer language most frequently-used to write computer programs are so called “programming languages” such as C, C++, Python, etc. Other common computer languages sometimes used to write computer programs (usually alongside programming languages) include markup languages (like HTML and Markdown) and style sheet languages (like CSS). For example, the Atom text editor is written in CoffeeScript, HTML, JavaScript and CSS, where CoffeeScript and JavaScript are programming languages.

### Free and Open-Source Software

**Free and open-source software** (**FOSS**) refers to software who’s source code is licensed such that it can freely shared, distributed, studied and even modified and re-released by anyone. FOSS licenses usually require that anyone that modifies and re-releases the source code gives some recognition to the original authors of the source code and some licenses (which are called **copyleft** licenses) even require that the modified source code be released under a similar (if not identical) license to the original source code. The most popular copyleft license is the GNU General Public License (GPL), while the most popular non-copyleft (or **permissive**) FOSS licenses include the BSD licenses and the MIT License.

### Proprietary Software

**Proprietary software** (**PS**) refers to software who’s source code is licensed such that it cannot be freely and legally shared. PS is usually, for charge, that is you have to pay to use them. Although some PS is so called “freeware”, in other words, you can use it for free, but you cannot freely and legally access the program’s source code.

### Fork

A **fork** or **project fork**, is when developers take a copy of the source code from one software project and start independently working on it (or developing it) themselves. In the FOSS world this is commonplace due to the relative lack of restrictions imposed by FOSS licenses.

### Downstream / Upstream

The terms **downstream** and **upstream** refers to the direction from and toward the original authors or maintainers of software that is distributed as source code, respectively.

### Back-End / Front-End

The terms **back-end** and **front-end** are used together to refer to a relationship between two programs. The front-end program runs the back-end program in the background (often without the user noticing), to perform a specified action (usually package management on this site), but usually the front-end has some higher-level features that it brings to the table, that the back-end program lacks. Quite often, on this site, I will refer to graphical package managers as being front-ends for a command-line package manager, which the graphical package manager will run in the background. What the graphical package manager brings to the table is a more intuitive user interface.

### Operating System

An **operating system** (**OS**) is the base set of system software that forms the foundation for other programs to run on top of. It manages all communication between the computer’s hardware and the application software that run on top of it. At its heart, each OS has what is known as a kernel, which manages all communication with the computer’s hardware. Notable examples of operating systems, include:

- FreeBSD
- Linux
- Mac OS
- MS-DOS
- OS X
- Windows 1.0 to Windows ME (including Windows 95 and 98)
- Windows NT (including Windows XP, Vista, 7, 8, 10, etc)

### Kernel

An operating system **kernel** is the piece of system software that manages all communication between a computer’s hardware and its software. Most kernels also perform virtual memory allocation. Some of this virtual memory is allocated to the kernel (which is called **kernel mode**), the rest is allocated to the user’s processes (or **user mode**, application software run in user mode). It is in many ways the operating system’s brain, without it the OS will not work. There are three main types of operating system kernel, based on their respective design:

- **Hybrid kernel** — as its name suggest it is mid-way between the below designs. Examples include the kernels of OS X and Windows NT. Linus Torvalds, the lead and original developer of the Linux kernel, amongst others, believe that the **hybrid kernel** category is purely marketing and that these kernels fit quite easily into one of the following two categories.

- **Microkernel** (or **μkernel**) — kernels that keep as few processes running in kernel mode as possible. They, as their name suggest, usually do the bare minimum needed of a kernel. Consequently, the number of lines of code in their source code is usually substantially less than their monolithic counterparts. Extreme variants of microkernels include nanokernels and picokernels, which have even fewer lines of source code. The most notable example is MINIX.

- **Monolithic kernel** — these are kernels that perform all operating system functions in kernel mode. They usually consist of far more lines of code than their microkernel counterparts. The most notable examples are the FreeBSD, Linux, NetBSD and OpenBSD kernels.

Microkernels are easier for software developers to work on and are supposedly more easily portable to additional instruction set architectures (ISAs). Despite this, the monolithic Linux kernel has been ported to the greatest number of ISAs of any operating system kernel.

### Unix

**Unix** (or **UNIX** for the trademark) is a family of operating systems that share several common characteristics and are certified as being compliant to at least one version of the **Single UNIX Specification** (**SUS**). These common characteristics are best summarized with what is sometimes called the “**Unix philosophy**”. The Unix philosophy is that the operating system provides a set of simple command-line tools or utilities (which I will sometimes refer to as Unix utilities) that perform a limited, well-defined function, which usually involves manipulating components (like files) in the unified file system that is also characteristic of Unix systems. Additionally Unix systems also have what is known as a command language or shell scripting language, called a **Unix shell**, with which users can call on these simple tools. Unix is also notable in that it is designed to be easily portable to a variety of different computers (distinguished from one another, mostly by the details of their CPU).

### Unix-like

A **unix-like** operating system is one that behaves and to all the world seems like a Unix system, despite not being certified compliant to any version of the SUS. These systems can also be referred to as Unix clones. The only real practical difference between Unix and Unix-like systems are that Unix systems are usually developed by a commercial entity with the funds required to get their system SUS-certified.

### \*nix

**\*nix** is my shorthand way of referring collectively to both Unix and Unix-like systems. Despite this, you will also see other authors, including those that know far more than I do about these systems, using \*nix to refer to just Unix-like systems.

### Linux

**Linux** is a large family of Unix-like operating systems (its members are referred to, collectively, as Linux distributions) that share one common defining characteristic: they use the Linux kernel as their kernel. The Linux kernel is a predominantly free and open-source kernel developed by Linus Torvalds who first started developing the kernel in 1991 when he was a 21-year-old computer science student studying at the University of Helsinki in Finland. I used the phrasing “predominantly free and open-source” deliberately, as while most of the kernel’s source code is licensed under the GNU GPL, there are some binary blobs on the kernel (which mostly just add to its compatibility with available hardware) that are not free and open-source.

### GNU

The **GNU Project** is a FOSS project that was first founded in the 1980s by Richard M. Stallman (or rms), its stated mission is to develop a free and open-source Unix clone. This clone is referred to as GNU, which is incredibly unpopular. The GNU Project provides the Unix utilities (contained in the GNU Coreutils package) and the Unix shell (called Bash) used by the vast majority of Linux distributions. Due to this some people refer to the family of operating systems known as Linux, as GNU/Linux.

### Free Software Foundation

The **Free Software Foundation** (**FSF**) non-profit organization set up by Stallman that advocates the widespread use of FOSS and was originally set up to hire people to develop software for the GNU Project. The FSF also provides its own set of predominantly copyleft licenses which includes the GNU GPL mentioned earlier.

### Linux-libre

The **Linux-libre kernel** is essentially the Linux kernel with its binary blobs removed. This makes the kernel entirely free and open-source, as these binary blobs are proprietary software. A comparatively small number of Linux distributions use the libre kernel, these distributions are often called GNU/Linux-libre distributions and are fairly unpopular compared to their non-libre counterparts.

### Berkeley Software Distribution

The **Berkeley Software Distribution** (**BSD**) is a Unix operating system that was developed at the University of California, Berkeley between 1977 and 1995. It was originally closed-source (that is, not open-source), but later releases were licensed under permissive BSD licenses. Since then several descendants of BSD have emerged with the most notable and popular one being FreeBSD. I use the terminology \*BSD to collectively refer to BSD and its descendants.

### File Archive

A **file archive** is a type of file, that stores one or more files, potentially with associated metadata, in a more portable and easily-compressed format. On Linux and other *nix systems, the most common type of file archive is a tar archive (which have the `.tar` file extension), with rar archives (file extension: `.rar`) being a popular alternative, especially for non-Linux platforms such as Windows. `tar` is a basic Unix utility, the specifics of this utility, its syntax, supported file formats, etc. is dependent on the *nix system it belongs to. Most Linux distributions use GNU tar as their default tar utility, but also have FreeBSD’s tar (usually called by the `bsdtar` command) utility available from their software repositories.

### Software Package

Software packages are distributions (or packages) of software and data contained within a file archive. This archive is sometimes compressed so as to save space and make them easier to transfer over a network. Software packages usually also contain some metadata, that is, information about the contents of the package. Example software package formats include:

- Debian package format (file extension: `.deb`) — used by Debian’s dpkg package manager. They are archives created using the Unix `ar` utility.
- pacman package format (file extension: `.pkg.tar.xz`) — used by Arch Linux and other Linux distributions using the pacman package manager. They are xz-compressed tar archives.
- RPM package format (file extension: `.rpm`) — used by Red Hat’s RPM package manager.

### Package Management System

A **package management system** (**PMS**, plural form: **PMSs**) or **package manager** is a collection of system software that automates the process of installing, configuring, removing and upgrading software packages. Traditionally Linux PMSs were operated solely from the command-line but nowadays several graphical PMSs also exist.

### Software Repository

A **software repository** is essentially an archive of software packages from which package managers can download said packages and then install them.

### Linux Distribution

A **Linux distribution** (**LD** or **distro**) is an individual, specific, operating system that uses the Linux kernel (that is, a specific member of the Linux family of operating systems). Most Linux distributions use GNU Project software for their Unix utilities, hence meaning that most Linux distributions can also be called **GNU/Linux distributions**. An LD consists of, at least, the following basic components:

- The **Linux kernel** (or the **Linux-libre kernel**, in some cases)
- **GNU Project software**, such as Bash, the coreutils package, glibc, _etc_.
- A **package management system**, such as APT, DNF, Entropy, pacman, Portage, _etc_.

### Software Version Nomenclature

In the field of software development, software releases are usually distinguished from one another by use of a numbering scheme. Each project has a different numbering scheme. The most common scheme is of the form:

- `x.y.z`. `x`, `y` and `z` are all natural numbers (that is, `x`, `y`, `z` ∈ `{0, 1, 2, 3, ...}`). `x` is the major version of the software. Major versions have major feature differences in them, for example, the 4.0 Linux kernel had far more features than the 3.0 version of the Linux kernel. `y` is the minor version of the software. Minor software releases (where the only difference is the minor version number of the software. For example 4.6.0 is one minor release ahead of 4.5.0) usually only differ by a few, often minor features. `z` is the patch (or bug-fix) version of the software. If you are sick of my algebra I will give you an example of a program that follows this versioning scheme: the Linux kernel. An example version of the kernel is the 4.9.6 kernel. 4 is the major version, 9 is the minor version and 6 is the patch version.

### Release Models: Fixed vs. Rolling

In the context of operating system development, there are two main types of release model: fixed and rolling. The most popular of these is the fixed **release model**, with the rolling release model being mostly used by bleeding edge operating systems geared towards advanced users like Arch Linux and Gentoo Linux.

Operating systems that follow a **fixed release model** (**FRM**) have fixed releases, which users are required to upgrade to, in order to keep their system up-to-date. This upgrade process can be (1) via downloading or otherwise acquiring the installation media for the latest version and going through its installer, or (2) via the distribution’s package manager or other methods (e.g., Ubuntu uses the `do-release-upgrade` command). These upgrades usually include major updates for several pieces of software, including core system components like the kernel, C libraries, compilers, core utilities, etc. In my experience, this process takes hours, uses up a lot of bandwidth and usually breaks at least one program on one’s system. This is why I, personally, are not a big fan of systems following a FRM.

Systems following a **rolling release model** (**RRM**) have no fixed releases, rather software updates, including major ones, simply become available for installation as soon as they have been packaged by the repository’s maintainers.

### Virtualization

**Virtualization** is the act of creating a virtual (rather than actual) version of something. Most commonly this “something” is an operating system. Virtualization is usually performed using computer programs that can be referred to as virtualization programs. In this context, the **host** is the computer being used to run the virtualization program, while the **guest** is the virtual system being run. For example, I am presently typing this glossary section on Arch Linux, so if I fire up a CentOS 7 VM in Oracle VM VirtualBox, then my host operating system would be Arch Linux and my guest operating system would be CentOS 7.

### Cross-Distribution Package Formats

A **cross-distribution package format** (**CDPF**; plural form is **CDPFs**) are a type of Linux software package format that are designed to run on most, if not all, Linux distributions. There are four main, distinct CDPFs I am aware of:

- [**AppImage**](http://appimage.org/) (previously known as **klik**), a type of self-mounting image file (created using SquashFS) that contains all the libraries, executables, desktop configuration files, icon files, _etc_. used by the application it provides. They need no root privileges in order to be run and need no special package manager of their own, as unlike most package formats they are not installed. They are distinct from other CDPFs as they are not installed and unlike binary archives they need not be extracted in order to be run. They merely need to be marked as executable (with `chmod +x`) and run (with `./<AppImage>` where `<AppImage>` is the name of the AppImage, including its file extension. I have built quite a few AppImages, usually with the help of [Simon Peter](https://github.com/probonopd), the creator of this package format.

- **Binary archives**, which have been aroud for decades are essentially archives (usually zipped or otherwise compressed) which contain all the libraries and executables required to run the program they provide on Linux. They need to be extracted in order for the program contained within to be run. SageMath and Scilab are both programs that are distributed like this.

- [**Flatpak**](http://flatpak.org/) (previously known as **xdg-app**), a package format best supported (but not officially supported by) by the Fedora (for example, the `flatpak` package is in the official Fedora repositories) Linux distribution and the GNOME desktop environment. Most GNOME applications are officially available as Flatpaks. GNOME Software (a graphical front-end for package management) also has support for Flatpaks as of the 3.22.0 release. Flatpaks are installed using a package manager also known as Flatpak and called by the command `flatpak`. As one can probably guess one has to install the Flatpak package manager using your distribution’s respective package manager (e.g., APT, DNF, pacman, URPMI, Yum, ZYpp) in order to use it to install Flatpak packages. The only distributions I know of with Flatpak in its official repositories are: Arch Linux, Fedora and Manjaro Linux. CentOS, Debian, Gentoo, openSUSE and Ubuntu users have to use unofficial repositories in order to install it. Like most package managers, Flatpak requires administrative privileges in order to be run. Flatpaks are perhaps the most challenging package format to build, in my opinion.

- [**Snap**](http://snapcraft.io/), a package format officially developed by Canonical Ltd, the same company responsible for the development of the Ubuntu operating system. Like Flatpak it also requires its own package manager to be installed in order for one to run them. This package manager is written in Google’s Go programming language (which was first publically released in 2009, so it is fairly new). Snap packages are built using a program called `snapcraft` which is written in Python. The source files used to tell `snapcraft` how to build Snap packages and the metadata to include with them are yaml files that often call on plugins (written in Python) in order to build the Snap package. I have never built a Snap package from scratch as I do not understand Python well enough to write my own plugins, but I have managed to create custom packages using existing source files.

### Governance

In the context of open-source projects, the term **governance** refers to how the project is governed or lead. Some projects are **authoritarian** in governance, in other words they are dictatorships, with a single leader in charge. A notable example of such a project is the Slackware Linux Project. Others are **donation-sponsored democracies**, wherein the volunteer developers of the project usually have the power to make decisions via consensus. Likewise others are **company-sponsored semi-democracies**, wherein a company sponsors the project and has some say over decisions, but the majority of the authority to make decisions about the project resides with the community of volunteer developers (or so it should, whether it does in practise is something I will likely not know until I work in one).

## Acronyms

> **NOTE**
>
> > - _Acronyms covered in the previous sections are not repeated in this list._
>
> > - _Hyperlinks are to sources that explain, in greater detail, the term._

- **ABS**: [**Arch Build System**](https://wiki.archlinux.org/index.php/Arch_Build_System), a system whereby all the PKGBUILDs, patch files and assorted other files used to build packages in the pacman repositories are stored in subdirectories of /var/abs. It is essentially Arch’s equivalent to the Portage Tree.
- **AUR**: [**Arch User Repository**](https://wiki.archlinux.org/index.php/Arch_User_Repository), a repository of Arch user-supplied PKGBUILDs, patch files and assorted other files that, while they are not used to build any packages in the pacman repositories, can (provided they do not have any bugs preventing them from building successfully, that is) be used to build Arch packages locally (on their own Arch machine) by users.
- **Deb**: the package format used by Debian’s dpkg package manager.
- **PC**: **Personal computer**. Can be a desktop or laptop, does not matter if it once ran OS X or Windows, still to me it is a PC.
- **RPM**: [**RPM Package Manager**](http://rpm.org/), originally **Red Hat Package Manager**. This is the name of both a package manager and the package format used by this package manager.
