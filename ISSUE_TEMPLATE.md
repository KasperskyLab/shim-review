Make sure you have provided the following information:

 - [x] link to your code branch cloned from rhboot/shim-review in the form user/repo@tag  
https://github.com/KasperskyLab/shim-review/tree/KasperskyLab-shim-x86_64-20181102
 - [x] completed README.md file with the necessary information  
https://github.com/KasperskyLab/shim-review/blob/KasperskyLab-shim-x86_64-20181102/README.md
 - [x] shim.efi to be signed  
https://github.com/KasperskyLab/shim-review/blob/KasperskyLab-shim-x86_64-20181102/shimx64.efi
 - [x] public portion of your certificate embedded in shim (the file passed to VENDOR_CERT_FILE)  
https://github.com/KasperskyLab/shim/blob/shim_15_kl_patch_tag/KLBOOTEV_2018.cer
 - [x] any extra patches to shim via your own git tree or as files  
https://github.com/KasperskyLab/shim/tree/shim_15_kl_patch_tag
 - [x] any extra patches to grub via your own git tree or as files  
N/A
 - [x] build logs  
https://github.com/KasperskyLab/shim-review/blob/KasperskyLab-shim-x86_64-20181102/build.log


###### What organization or people are asking to have this signed:
Kaspersky Lab.

###### What product or service is this for:
Kaspersky Lab’s products.

###### What is the origin and full version number of your shim?
https://github.com/rhboot/shim/tree/15

###### What's the justification that this really does need to be signed for the whole world to be able to boot it:
Kaspersky Shim is a common component for some of Kaspersky Lab’s products.
It loads a universal plugin manager for various features: Full disk encryption, Rescue Disk and Early boot protection component.

###### How do you manage and protect the keys used in your SHIM?
Private key is stored in hardware module with controlled access.

###### Do you use EV certificates as embedded certificates in the SHIM?
Yes.

###### What is the origin and full version number of your bootloader (GRUB or other)?
GRUB or Linux kernel is not used.

This build of shim will be used to load and verify our custom preboot components.
Windows loader will be launched after that.

###### If your SHIM launches any other components, please provide further details on what is launched
Full disk encryption, Rescue Disk, Early boot protection component.

###### How do the launched components prevent execution of unauthenticated code?
All our components are signed with authenticode signatures and always verified during loading.
Windows loader is signed by Microsoft, it launched with LoadImage/StartImage and will be verified by firmware when SecureBoot is on.

###### Does your SHIM load any loaders that support loading unsigned kernels (e.g. GRUB)?
No.

###### What kernel are you using? Which patches does it includes to enforce Secure Boot?
We launch Windows loader and kernel.

###### What changes were made since your SHIM was last signed?
This is first submission.

###### What is the hash of your final SHIM binary?
414065ca4238bfff0ce2601ac4ac924bc8da98b0b75c0a81cde78f05f5de869a
