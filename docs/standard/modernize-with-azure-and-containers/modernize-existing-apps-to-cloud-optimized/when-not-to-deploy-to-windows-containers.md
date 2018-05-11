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
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Kiedy nie należy wdrażać na kontenery systemu Windows

Niektóre technologie systemu Windows nie są obsługiwane przez kontenery systemu Windows. W takich przypadkach nadal należy przeprowadzić migrację do maszyn wirtualnych standardy, zwykle za pomocą tylko systemu Windows i usługi IIS.

Przypadków nie jest obsługiwana w kontenerach systemu Windows, począwszy od 2018 może: 

-   Usługi kolejkowania wiadomości firmy Microsoft (MSMQ) aktualnie jest dostępna tylko w kontenerach systemu Windows oparte na wersji v1803 systemu Windows Server, ale nie w poprzednich wersjach. 

    -   [Forum żądania UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [Forum dyskusyjne](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Koordynator transakcji rozproszonych (MSDTC) nie jest obecnie obsługiwane w kontenerach systemu Windows.

    -   [Problem GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office nie obsługuje obecnie kontenerów.

    -   [Forum żądania UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   Aplikacje interfejsu użytkownika (aplikacje klienckie za pomocą interfejsu użytkownika programu visual) nie są obsługiwane scenariusze.

-   Role systemu Windows infrastruktury (DNS, DHCP, kontroler domeny, NTP, drukowania, serwer plików, IAM itp.) nie są obsługiwane scenariusze.


Żądania od społeczności i dodatkowe scenariusze obsługiwane nie, zobacz forum usługi UserVoice dla kontenerów systemu Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Maszyny wirtualne i kontenerów na platformie Azure**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[Poprzednie](deploy-existing-net-apps-as-windows-containers.md)
[dalej](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
