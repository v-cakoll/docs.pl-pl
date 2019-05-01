---
title: Kiedy nie należy wdrażać kontenerów systemu Windows
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kiedy nie należy wdrażać kontenery Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: c5d8f50c7b9967eba0ec01c9e864a02b6a3b201a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012012"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="32d0d-103">Kiedy nie należy wdrażać kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="32d0d-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="32d0d-104">Niektóre technologie Windows nie są obsługiwane przez kontenery Windows.</span><span class="sxs-lookup"><span data-stu-id="32d0d-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="32d0d-105">W takich przypadkach nadal należy przeprowadzić migrację do maszyn wirtualnych standardy, zwykle przy użyciu tylko Windows i usług IIS.</span><span class="sxs-lookup"><span data-stu-id="32d0d-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="32d0d-106">W przypadkach nie jest obsługiwana w kontenerach Windows, począwszy od maja 2018 r.:</span><span class="sxs-lookup"><span data-stu-id="32d0d-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="32d0d-107">Microsoft usługi kolejkowania komunikatów (MSMQ) obecnie jest dostępna tylko w kontenerach Windows oparte na wersji v1803 systemu Windows Server, ale nie w poprzednich wersjach.</span><span class="sxs-lookup"><span data-stu-id="32d0d-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="32d0d-108">Forum żądania UserVoice</span><span class="sxs-lookup"><span data-stu-id="32d0d-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="32d0d-109">Forum dyskusyjne</span><span class="sxs-lookup"><span data-stu-id="32d0d-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="32d0d-110">Transakcji Koordynator MSDTC (Microsoft Distributed) nie jest obecnie obsługiwane w kontenerach Windows.</span><span class="sxs-lookup"><span data-stu-id="32d0d-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="32d0d-111">Problem w usłudze GitHub</span><span class="sxs-lookup"><span data-stu-id="32d0d-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="32d0d-112">Microsoft Office nie jest obecnie obsługiwane kontenerów.</span><span class="sxs-lookup"><span data-stu-id="32d0d-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="32d0d-113">Forum żądania UserVoice</span><span class="sxs-lookup"><span data-stu-id="32d0d-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="32d0d-114">Interfejs użytkownika aplikacji (aplikacje klienckie za pomocą interfejsu użytkownika programu visual) nie są obsługiwane scenariusze.</span><span class="sxs-lookup"><span data-stu-id="32d0d-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="32d0d-115">Windows rolami infrastruktury (DNS, DHCP, kontroler domeny, NTP, drukowania, serwer plików, zarządzanie dostępem i Tożsamościami itp.) nie są obsługiwane scenariusze.</span><span class="sxs-lookup"><span data-stu-id="32d0d-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="32d0d-116">Dodatkowe scenariusze nieobsługiwane i żądań od społeczności można znaleźć UserVoice forum dla kontenerów Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="32d0d-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="32d0d-117">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="32d0d-117">Additional resources</span></span>

- <span data-ttu-id="32d0d-118">**Maszyny wirtualne i kontenery na platformie Azure**</span><span class="sxs-lookup"><span data-stu-id="32d0d-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="32d0d-119">[Poprzednie](deploy-existing-net-apps-as-windows-containers.md)
> [dalej](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="32d0d-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
