---
title: Kiedy należy wdrażać kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrażać kontenery systemu Windows na maszynach wirtualnych platformy Azure (w chmurze IaaS)
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676899"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Kiedy należy wdrażać kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)

Jeśli twoja organizacja korzysta z maszyn wirtualnych platformy Azure, nawet jeśli używasz kontenerów systemu Windows, nadal masz do czynienia z systemem IaaS. Oznacza to, że do czynienia z operacjami infrastruktury, poprawki os maszyny wirtualnej i złożoności infrastruktury dla aplikacji o wysokiej skalowalności, gdy trzeba wdrożyć na wielu maszynach wirtualnych w infrastrukturze z równoważeniem obciążenia. Główne scenariusze korzystania z kontenerów systemu Windows w maszynie wirtualnej platformy Azure to:

- **Środowisko dewelopersko-testowe:** Maszyna wirtualna w chmurze jest idealna do tworzenia i testowania w chmurze. W zależności od potrzeb można szybko utworzyć lub zatrzymać środowisko.

- **Małe i średnie potrzeby skalowalności**: W scenariuszach, w których może być potrzebne tylko kilka maszyn wirtualnych dla środowiska produkcyjnego, zarządzanie niewielką liczbą maszyn wirtualnych może być przystępne, dopóki nie można przejść do bardziej zaawansowanych środowisk PaaS, takich jak koordynatorzy.

- **Środowisko produkcyjne z istniejącymi narzędziami wdrażania**: Być może przenosisz się ze środowiska lokalnego, w którym zainwestowano w narzędzia do tworzenia złożonych wdrożeń na maszynach wirtualnych lub serwerach bez systemu (takich jak puppet lub podobne narzędzia). Aby przejść do chmury przy minimalnych zmianach w procedurach wdrażania środowiska produkcyjnego, można nadal używać tych narzędzi do wdrażania na maszynach wirtualnych platformy Azure. Jednak należy użyć kontenerów systemu Windows jako jednostki wdrażania, aby poprawić środowisko wdrażania.

>[!div class="step-by-step"]
>[Poprzedni](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[następny](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
