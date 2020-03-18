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
# <a name="when-not-to-deploy-to-windows-containers"></a>Kiedy nie należy wdrażać kontenerów systemu Windows

Niektóre technologie systemu Windows nie są obsługiwane przez kontenery systemu Windows. W takich przypadkach nadal trzeba przeprowadzić migrację do maszyn wirtualnych standardów, zwykle tylko z systemami Windows i usługAmi IIS.

Przypadki nieobsługiwane w kontenerach systemu Windows od maja 2018 r.:

- Usługa kolejkowania wiadomości firmy Microsoft (MSMQ) jest obecnie dostępna tylko w kontenerach systemu Windows na podstawie wersji systemu Windows Server v1803, ale nie w innych wcześniejszych wersjach.

  - [Forum z prośbą uservoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Forum dyskusyjne](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Koordynator transakcji rozproszonych firmy Microsoft (MSDTC) nie jest obecnie obsługiwany w kontenerach systemu Windows.

  - [Problem z githubem](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Pakiet Microsoft Office obecnie nie obsługuje kontenerów.

  - [Forum z prośbą uservoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Aplikacje interfejsu użytkownika (aplikacje klienckie z wizualnym interfejsem użytkownika) nie są obsługiwane scenariusze.

- Role infrastruktury systemu Windows (DNS, DHCP, DC, NTP, PRINT, Serwer plików, IAM itp.) nie są obsługiwane scenariusze.

Dodatkowe nieobsługiwane scenariusze i żądania społeczności można znaleźć na forum UserVoice dla kontenerów systemu Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Maszyny wirtualne i kontenery na platformie Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Poprzedni](deploy-existing-net-apps-as-windows-containers.md)
> [następny](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
