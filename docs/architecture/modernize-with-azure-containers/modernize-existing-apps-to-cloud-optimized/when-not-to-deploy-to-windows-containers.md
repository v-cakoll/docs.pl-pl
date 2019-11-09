---
title: Kiedy nie należy wdrażać kontenerów systemu Windows
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Gdy nie należy wdrażać kontenerów systemu Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676914"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Kiedy nie należy wdrażać kontenerów systemu Windows

Niektóre technologie systemu Windows nie są obsługiwane przez kontenery systemu Windows. W takich przypadkach nadal trzeba przeprowadzić migrację do standardowych maszyn wirtualnych, zazwyczaj z systemem Windows i usługami IIS.

Przypadki nieobsługiwane w kontenerach systemu Windows, od maja 2018:

- Usługa kolejkowania komunikatów (MSMQ) firmy Microsoft jest obecnie dostępna tylko w kontenerach systemu Windows opartych na systemie Windows Server v1803 Release, ale nie w innych wcześniejszych wersjach.

  - [Forum żądania UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Forum dyskusyjne](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Usługa Microsoft Distributed Transaction Coordinator (MSDTC) nie jest obecnie obsługiwana w kontenerach systemu Windows.

  - [Problem z usługą GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office obecnie nie obsługuje kontenerów.

  - [Forum żądania UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Aplikacje interfejsu użytkownika (aplikacje klienckie z interfejsem użytkownika Visual) nie są obsługiwane.

- Role infrastruktury systemu Windows (DNS, DHCP, DC, NTP, PRINT, serwer plików, IAM itp.) nie są obsługiwane w scenariuszach.

Aby zapoznać się z dodatkowymi nieobsługiwanymi scenariuszami i żądaniami ze społeczności, zobacz Forum usługi UserVoice dla kontenerów systemu Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Maszyny wirtualne i kontenery na platformie Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Poprzedni](deploy-existing-net-apps-as-windows-containers.md)
> [dalej](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
