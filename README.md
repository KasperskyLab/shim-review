This repo is for review of requests for signing shim.  To create a request for review:

- clone this repo
- edit the template below
- add the shim.efi to be signed
- add build logs
- commit all of that
- tag it with a tag of the form "myorg-shim-arch-YYYYMMDD"
- push that to github
- file an issue at https://github.com/rhboot/shim-review/issues with a link to your branch

Note that we really only have experience with using grub2 on Linux, so asking
us to endorse anything else for signing is going to require some convincing on
your part.

Here's the template:

-------------------------------------------------------------------------------
What organization or people are asking to have this signed:
-------------------------------------------------------------------------------
Kaspersky Lab.

-------------------------------------------------------------------------------
What product or service is this for:
-------------------------------------------------------------------------------
Kaspersky Lab’s products.

-------------------------------------------------------------------------------
What's the justification that this really does need to be signed for the whole world to be able to boot it:
-------------------------------------------------------------------------------
Kaspersky Shim is a common component for some of Kaspersky Lab’s products.
It loads a universal plugin manager for various features: Full disk encryption, Rescue Disk and Early boot protection component.

-------------------------------------------------------------------------------
Who is the primary contact for security updates, etc.
-------------------------------------------------------------------------------
- Name: Alexey Veselov
- Position: Senior Developer
- Email address: alexey.veselov@kaspersky.com
- PGP key: N/A

-------------------------------------------------------------------------------
Who is the secondary contact for security updates, etc.
-------------------------------------------------------------------------------
- Name: Vitaly Alexeev
- Position: Head of Data Encryption Development
- Email address: vitaly.alexeev@kaspersky.com
- PGP key: N/A

-------------------------------------------------------------------------------
What upstream shim tag is this starting from:
-------------------------------------------------------------------------------
https://github.com/rhboot/shim/tree/15

-------------------------------------------------------------------------------
URL for a repo that contains the exact code which was built to get this binary:
-------------------------------------------------------------------------------
https://github.com/KasperskyLab/shim/tree/shim_15_kl_patch_tag

-------------------------------------------------------------------------------
What patches are being applied and why:
-------------------------------------------------------------------------------
- Add build scripts and our certificate
- Fix null pointer dereference and memory leaks in errlog
- Force signature checking

Some code that will not be used in our scenarios was removed:

- Disable MOK support
- Disable load options, always use hardcoded loader path
- Disable fallback support
- Disable netboot and httpboot

-------------------------------------------------------------------------------
What OS and toolchain must we use to reproduce this build?  Include where to find it, etc.  We're going to try to reproduce your build as close as possible to verify that it's really a build of the source tree you tell us it is, so these need to be fairly thorough. At the very least include the specific versions of gcc, binutils, and gnu-efi which were used, and where to find those binaries.
-------------------------------------------------------------------------------
Build was performed inside of docker container. Ubuntu 18.04.1 LTS was used as host for docker.
Build scripts (Dockerfile, kl_build.sh) attempt to recreate following build environment:

- Ubuntu 18.04.1 LTS
- gcc (Ubuntu 7.3.0-27ubuntu1~18.04) 7.3.0
- GNU ld (GNU Binutils for Ubuntu) 2.30
- gnu-efi 3.0.8-0ubuntu1~18.04.1

To reproduce the build you can use following commands:
```
git clone https://github.com/KasperskyLab/shim.git
cd shim
git checkout shim_15_kl_patch_tag
chmod +x ./kl_build.sh
./kl_build.sh
```

Compiled binary and build.log will be located in the `out` directory.

-------------------------------------------------------------------------------
Which files in this repo are the logs for your build?   This should include logs for creating the buildroots, applying patches, doing the build, creating the archives, etc.
-------------------------------------------------------------------------------
build.log

-------------------------------------------------------------------------------
Add any additional information you think we may need to validate this shim
-------------------------------------------------------------------------------
N/A
