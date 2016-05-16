---
title: System Requirements  and Installation
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4a8b42d7-9fe5-4efe-9ea1-ace2131fe068
---
# System Requirements  and Installation
This topic addresses the information you need to install [!INCLUDE[winthreshold_server_1](includes/winthreshold_server_1_md.md)]. We use the following terms to distinguish among different actions, any of which could be involved in a new [!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)] deployment.

-   **Installation** is the basic concept of getting the new operating system on your hardware. Specifically, a **clean installation** requires deleting the previous operating system. Clean installation is the only supported option for this release

-   **Upgrade** means moving from your existing operating system to [!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)], while staying on the same hardware. For this release, upgrade to or from [!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)] is not supported

-   **Migration** means moving from your existing operating system to [!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)] by transferring to a different set of hardware. For this release, migration is not supported.

> [!WARNING]
> In this release, only clean installations are supported.
> 
> In this release, you cannot mount ReFS volumes formatted by using Windows Server 2016 Technical Preview 3. These volumes will appear as "raw," though the data is intact.  If you need to recover data from those volumes, mount them using Windows Server 2016 Technical Preview 3. ReFS volumes formatted by using Windows Server 2012, Windows Server 2012 R2, or Windows Server 2016 Technical Preview 4 can be mounted in this release without issues.

> [!NOTE]
> If at the time of installation, you choose to install with the Server Core option, you should be aware that no GUI components are installed at all and you will not be able to install or uninstall them with Server Manager. If you need GUI features, be sure to choose the "Server with Desktop Experience" option when you install [!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)]. For more information, see [Getting Started with Nano Server](Getting-Started-with-Nano-Server.md)

> [!IMPORTANT]
> For this release, use these product keys:
> 
> -   Windows Server Edition Family \(Datacenter\): 6XBNX\-4JQGW\-QX6QG\-74P76\-72V67
>-   Windows Server Edition Family \(Standard\): MFY9F\-XBN2F\-TYFMP\-CCV49\-RMYVH
> -   Windows Server Essentials: NYK9H-Y2FDB-2XKGC-F2XHK-WTT88

[comment]: # (ID: 362; Submitter: milanp; state: signed off)
> [!IMPORTANT]
> Install Cumulative Update for Windows Server 2016 Technical Preview 5 (KB3157663) before installing any server roles, features, or other products.
>
>If you install roles before installing the update, a variety of issues can occur. If this happens, reinstall the preview release and then immediately install the update.

## Review system requirements
The following are estimated system requirements for the [!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)]. If your computer has less than the "minimum" requirements, you will not be able to install this product correctly. Actual requirements will vary based on your system configuration and the applications and features you install.

> [!IMPORTANT]
> The highly diverse scope of potential deployments makes it unrealistic to state “recommended” system requirements that would be generally applicable. Consult documentation for each of the server roles you intend to deploy for more details about the resource needs of particular server roles. For the best results, conduct test deployments to determine appropriate system requirements for your particular deployment scenarios.

## Processor
Processor performance depends not only on the clock frequency of the processor, but also on the number of processor cores and the size of the processor cache. The following are the processor requirements for this product:

**Minimum**:
- 1.4 GHz 64\-bit processor
- Compatible with x64 instruction set
- Supports NX and DEP
- Supports CMPXCHG16b, LAHF/SAHF, and PrefetchW
- Supports Second Level Address Translation (EPT or NPT)


## RAM
The following are the estimated RAM requirements for this product:

**Minimum**:
- 512 MB
- ECC (Error Correcting Code) type or similar technology

> [!IMPORTANT]
> If you create a virtual machine with the minimum supported hardware parameters \(1 processor core and 512 MB RAM\) and then attempt to install this release on the virtual machine, Setup will fail.
> 
> To avoid this, do one of the following:
> 
> -   Allocate more than 800 MB RAM to the virtual machine you intend to install this release on. Once Setup has completed, you can change the allocation to as little as 512 MB RAM, depending on the actual server configuration.
> -   Interrupt the boot process of this release on the virtual machine with SHIFT\+F10. In the command prompt that opens, use Diskpart.exe to create and format an installation partition. Run **Wpeutil createpagefile \/path\=C:\\pf.sys** \(assuming the installation partition you created was C:\). Close the command prompt and proceed with Setup.

## Storage controller and disk space requirements
Computers that run Windows Server 2016 Technical Preview must include a storage adapter that is compliant with the PCI Express architecture specification. Persistent storage devices on servers classified as hard disk drives must not be PATA. Windows Server 2016 Technical Preview does not allow ATA/PATA/IDE/EIDE for boot, page, or data drives.

The following are the estimated **minimum** disk space requirements for the system partition.

**Minimum**: 32 GB

   > [!NOTE]
    > Be aware that 32 GB should be considered an *absolute minimum* value for successful installation. This minimum should allow you to install [!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)] in Server Core mode, with the Web Services \(IIS\) server role. A server in Server Core mode is about 4 GB smaller than the same server in Server with a GUI mode. For the smallest possible installation footprint, start with a Server Core installation and then completely remove any server roles or features you do not need by using Features on Demand. For more information about Server Core and Minimal Server Interface modes, see [Windows Server Installation Options](assetId:///ebbecbda-3d97-48fe-9599-4031ad285384).
    > 
    > The system partition will need extra space for any of the following circumstances:
    > 
    > -   If you install the system over a network.
    > -   Computers with more than 16 GB of RAM will require more disk space for paging, hibernation, and dump files.

## Network adapter requirements

Network adapters used with this release should include these features:

**Minimum**:
- An Ethernet adapter capable of at least gigabit throughput
- Compliant with the PCI Express architecture specification.
- Supports Pre-boot Execution Environment (PXE).

A network adapter that supports network debugging (KDNet) is useful, but not a minimum requirement. 



## Other requirements
Computers running this release also must have the following:


-   DVD drive \(if you intend to install the operating system from DVD media\)

The following items are not strictly required, but are necessary for certain features:

- UEFI 2.3.1c-based system and firmware that supports secure boot
- Trusted Platform Module

-   Graphics device and monitor capable of Super VGA \(1024 x 768\) or higher\-resolution

-   Keyboard and Microsoft® mouse \(or other compatible pointing device\)

-   Internet access \(fees may apply\)

>[!NOTE]
> A Trusted Platform Module (TPM) chip is not strictly required to install this release, though it is necessary in order to use certain features such as BitLocker Drive Encryption. If your computer uses TPM, it must meet these requirements:
>
>- Hardware-based TPMs must implement version 2.0 of the TPM specification.
>- TPMs that implement version 2.0 must have an EK certificate that is >either pre-provisioned to the TPM by the hardware vendor or be capable of >being retrieved by the device during the first boot.
>- TPMs that implement version 2.0 must ship with SHA-256 PCR banks and >implement PCRs 0 through 23 for SHA-256. It is acceptable to ship TPMs >with a single switchable PCR bank that can be used for both SHA-1 and >SHA-256 measurements.
>- A UEFI option to turn off the TPM is not a requirement.

## Installation of Nano Server
For detailed steps to install Windows Server 2016 as a Nano Server, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx)




