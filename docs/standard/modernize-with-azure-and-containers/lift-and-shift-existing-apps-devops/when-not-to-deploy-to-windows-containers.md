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
# <a name="when-not-to-deploy-to-windows-containers"></a>Kiedy nie należy wdrażać na kontenery systemu Windows

Niektóre technologie systemu Windows nie są obsługiwane przez kontenery systemu Windows. W takich przypadkach nadal należy przeprowadzić migrację do maszyn wirtualnych standardy, zwykle za pomocą tylko systemu Windows i usługi IIS.

Nieobsługiwane w kontenerach systemu Windows, począwszy od połowy 2017 przypadkach:

-   Usługi kolejkowania wiadomości firmy Microsoft (MSMQ) nie jest obecnie obsługiwane w kontenerach systemu Windows.

    -   [Forum żądania UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [Forum dyskusyjne](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Koordynator transakcji rozproszonych (MSDTC) aktualnie nie jest obsługiwana w kontenerach systemu Windows

    -   [Problem GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office nie obsługuje obecnie kontenerów

    -   [Forum żądania UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

Żądania od społeczności i dodatkowe scenariusze obsługiwane nie, zobacz forum usługi UserVoice dla kontenerów systemu Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Maszyny wirtualne i kontenerów na platformie Azure**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[Poprzednie](deploy-existing-net-apps-as-windows-containers.md)
[dalej](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
