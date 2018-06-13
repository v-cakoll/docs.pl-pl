---
title: Kiedy nie należy wdrażać na kontenery systemu Windows
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Kiedy nie należy wdrażać na kontenery systemu Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 819f32955ff019414bef8820d17d272eddc11bf8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958228"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="16520-103">Kiedy nie należy wdrażać na kontenery systemu Windows</span><span class="sxs-lookup"><span data-stu-id="16520-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="16520-104">Niektóre technologie systemu Windows nie są obsługiwane przez kontenery systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="16520-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="16520-105">W takich przypadkach nadal należy przeprowadzić migrację do maszyn wirtualnych standardy, zwykle za pomocą tylko systemu Windows i usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="16520-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="16520-106">Przypadków nie jest obsługiwana w kontenerach systemu Windows, począwszy od 2018 może:</span><span class="sxs-lookup"><span data-stu-id="16520-106">Cases not supported in Windows Containers, as of May 2018:</span></span> 

-   <span data-ttu-id="16520-107">Usługi kolejkowania wiadomości firmy Microsoft (MSMQ) aktualnie jest dostępna tylko w kontenerach systemu Windows oparte na wersji v1803 systemu Windows Server, ale nie w poprzednich wersjach.</span><span class="sxs-lookup"><span data-stu-id="16520-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span> 

    -   [<span data-ttu-id="16520-108">Forum żądania UserVoice</span><span class="sxs-lookup"><span data-stu-id="16520-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="16520-109">Forum dyskusyjne</span><span class="sxs-lookup"><span data-stu-id="16520-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="16520-110">Koordynator transakcji rozproszonych (MSDTC) nie jest obecnie obsługiwane w kontenerach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="16520-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="16520-111">Problem GitHub</span><span class="sxs-lookup"><span data-stu-id="16520-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="16520-112">Microsoft Office nie obsługuje obecnie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="16520-112">Microsoft Office currently does not support containers.</span></span>

    -   [<span data-ttu-id="16520-113">Forum żądania UserVoice</span><span class="sxs-lookup"><span data-stu-id="16520-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   <span data-ttu-id="16520-114">Aplikacje interfejsu użytkownika (aplikacje klienckie za pomocą interfejsu użytkownika programu visual) nie są obsługiwane scenariusze.</span><span class="sxs-lookup"><span data-stu-id="16520-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

-   <span data-ttu-id="16520-115">Role systemu Windows infrastruktury (DNS, DHCP, kontroler domeny, NTP, drukowania, serwer plików, IAM itp.) nie są obsługiwane scenariusze.</span><span class="sxs-lookup"><span data-stu-id="16520-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>


<span data-ttu-id="16520-116">Żądania od społeczności i dodatkowe scenariusze obsługiwane nie, zobacz forum usługi UserVoice dla kontenerów systemu Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="16520-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="16520-117">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="16520-117">Additional resources</span></span>

-   <span data-ttu-id="16520-118">**Maszyny wirtualne i kontenerów na platformie Azure**</span><span class="sxs-lookup"><span data-stu-id="16520-118">**Virtual machines and containers in Azure**</span></span>

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="16520-119">[Poprzednie](deploy-existing-net-apps-as-windows-containers.md)
[dalej](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="16520-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
