---
title: Kiedy nie należy wdrażać kontenerów systemu Windows
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy nie należy wdrażać w kontenerach systemu Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676914"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="d51c3-103">Kiedy nie należy wdrażać kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d51c3-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="d51c3-104">Niektóre technologie systemu Windows nie są obsługiwane przez kontenery systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d51c3-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="d51c3-105">W takich przypadkach nadal trzeba przeprowadzić migrację do maszyn wirtualnych standardów, zwykle tylko z systemami Windows i usługAmi IIS.</span><span class="sxs-lookup"><span data-stu-id="d51c3-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="d51c3-106">Przypadki nieobsługiwane w kontenerach systemu Windows od maja 2018 r.:</span><span class="sxs-lookup"><span data-stu-id="d51c3-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="d51c3-107">Usługa kolejkowania wiadomości firmy Microsoft (MSMQ) jest obecnie dostępna tylko w kontenerach systemu Windows na podstawie wersji systemu Windows Server v1803, ale nie w innych wcześniejszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d51c3-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="d51c3-108">Forum z prośbą uservoice</span><span class="sxs-lookup"><span data-stu-id="d51c3-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="d51c3-109">Forum dyskusyjne</span><span class="sxs-lookup"><span data-stu-id="d51c3-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="d51c3-110">Koordynator transakcji rozproszonych firmy Microsoft (MSDTC) nie jest obecnie obsługiwany w kontenerach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d51c3-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="d51c3-111">Problem z githubem</span><span class="sxs-lookup"><span data-stu-id="d51c3-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="d51c3-112">Pakiet Microsoft Office obecnie nie obsługuje kontenerów.</span><span class="sxs-lookup"><span data-stu-id="d51c3-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="d51c3-113">Forum z prośbą uservoice</span><span class="sxs-lookup"><span data-stu-id="d51c3-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="d51c3-114">Aplikacje interfejsu użytkownika (aplikacje klienckie z wizualnym interfejsem użytkownika) nie są obsługiwane scenariusze.</span><span class="sxs-lookup"><span data-stu-id="d51c3-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="d51c3-115">Role infrastruktury systemu Windows (DNS, DHCP, DC, NTP, PRINT, Serwer plików, IAM itp.) nie są obsługiwane scenariusze.</span><span class="sxs-lookup"><span data-stu-id="d51c3-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="d51c3-116">Dodatkowe nieobsługiwane scenariusze i żądania społeczności można znaleźć na forum UserVoice dla kontenerów systemu Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="d51c3-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d51c3-117">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="d51c3-117">Additional resources</span></span>

- <span data-ttu-id="d51c3-118">**Maszyny wirtualne i kontenery na platformie Azure**</span><span class="sxs-lookup"><span data-stu-id="d51c3-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="d51c3-119">[Poprzedni](deploy-existing-net-apps-as-windows-containers.md)
> [następny](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="d51c3-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
