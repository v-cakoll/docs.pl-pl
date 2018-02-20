---
title: "Kiedy nie należy wdrażać na kontenery systemu Windows"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Kiedy nie należy wdrażać na kontenery systemu Windows"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c74b71f9c80ab51cabe0e3c4abf32f292da30763
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="83b9f-103">Kiedy nie należy wdrażać na kontenery systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83b9f-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="83b9f-104">Niektóre technologie systemu Windows nie są obsługiwane przez kontenery systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="83b9f-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="83b9f-105">W takich przypadkach nadal należy przeprowadzić migrację do maszyn wirtualnych standardy, zwykle za pomocą tylko systemu Windows i usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="83b9f-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="83b9f-106">Nieobsługiwane w kontenerach systemu Windows, począwszy od połowy 2017 przypadkach:</span><span class="sxs-lookup"><span data-stu-id="83b9f-106">Cases not supported in Windows Containers, as of mid-2017:</span></span>

-   <span data-ttu-id="83b9f-107">Usługi kolejkowania wiadomości firmy Microsoft (MSMQ) nie jest obecnie obsługiwane w kontenerach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="83b9f-107">Microsoft Message Queuing (MSMQ) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="83b9f-108">Forum żądania UserVoice</span><span class="sxs-lookup"><span data-stu-id="83b9f-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="83b9f-109">Forum dyskusyjne</span><span class="sxs-lookup"><span data-stu-id="83b9f-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="83b9f-110">Koordynator transakcji rozproszonych (MSDTC) aktualnie nie jest obsługiwana w kontenerach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83b9f-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers</span></span>

    -   [<span data-ttu-id="83b9f-111">Problem GitHub</span><span class="sxs-lookup"><span data-stu-id="83b9f-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="83b9f-112">Microsoft Office nie obsługuje obecnie kontenerów</span><span class="sxs-lookup"><span data-stu-id="83b9f-112">Microsoft Office currently does not support containers</span></span>

    -   [<span data-ttu-id="83b9f-113">Forum żądania UserVoice</span><span class="sxs-lookup"><span data-stu-id="83b9f-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

<span data-ttu-id="83b9f-114">Żądania od społeczności i dodatkowe scenariusze obsługiwane nie, zobacz forum usługi UserVoice dla kontenerów systemu Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="83b9f-114">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="83b9f-115">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="83b9f-115">Additional resources</span></span>

-   <span data-ttu-id="83b9f-116">**Maszyny wirtualne i kontenerów na platformie Azure**</span><span class="sxs-lookup"><span data-stu-id="83b9f-116">**Virtual machines and containers in Azure**</span></span>

    [<span data-ttu-id="83b9f-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span><span class="sxs-lookup"><span data-stu-id="83b9f-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="83b9f-118">[Poprzednie](deploy-existing-net-apps-as-windows-containers.md)
[dalej](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="83b9f-118">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
