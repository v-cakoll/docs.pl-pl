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
# <a name="when-not-to-deploy-to-windows-containers"></a>Kiedy nie należy wdrażać kontenerów systemu Windows

Niektóre technologie Windows nie są obsługiwane przez kontenery Windows. W takich przypadkach nadal należy przeprowadzić migrację do maszyn wirtualnych standardy, zwykle przy użyciu tylko Windows i usług IIS.

W przypadkach nie jest obsługiwana w kontenerach Windows, począwszy od maja 2018 r.:

- Microsoft usługi kolejkowania komunikatów (MSMQ) obecnie jest dostępna tylko w kontenerach Windows oparte na wersji v1803 systemu Windows Server, ale nie w poprzednich wersjach.

  - [Forum żądania UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Forum dyskusyjne](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Transakcji Koordynator MSDTC (Microsoft Distributed) nie jest obecnie obsługiwane w kontenerach Windows.

  - [Problem w usłudze GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office nie jest obecnie obsługiwane kontenerów.

  - [Forum żądania UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Interfejs użytkownika aplikacji (aplikacje klienckie za pomocą interfejsu użytkownika programu visual) nie są obsługiwane scenariusze.

- Windows rolami infrastruktury (DNS, DHCP, kontroler domeny, NTP, drukowania, serwer plików, zarządzanie dostępem i Tożsamościami itp.) nie są obsługiwane scenariusze.

Dodatkowe scenariusze nieobsługiwane i żądań od społeczności można znaleźć UserVoice forum dla kontenerów Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Maszyny wirtualne i kontenery na platformie Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Poprzednie](deploy-existing-net-apps-as-windows-containers.md)
> [dalej](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
