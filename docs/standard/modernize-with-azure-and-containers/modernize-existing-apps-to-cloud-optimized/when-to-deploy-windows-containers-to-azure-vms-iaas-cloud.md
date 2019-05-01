---
title: Kiedy należy wdrażać kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kiedy należy wdrażać kontenery Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 51217e2c94fd9727c8f7907e791cdebaec98f14f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011960"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Kiedy należy wdrażać kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)

Jeśli Twoja organizacja używa w przypadku maszyn wirtualnych platformy Azure, nawet wtedy, gdy używana jest również kontenery Windows, wciąż się radzenia sobie z rozwiązania IaaS. Oznacza to, że zajmowanie się operacji infrastruktury, poprawek systemu operacyjnego maszyny Wirtualnej i złożoność infrastruktury dla aplikacji o wysokim stopniu skalowalności gdy należy wdrożyć wiele maszyn wirtualnych w infrastrukturze równoważenia obciążenia. Główne scenariusze dotyczące korzystania z kontenerów Windows w Maszynie wirtualnej platformy Azure są następujące:

- **Środowisko programistyczne/testowe**: Maszynę wirtualną w chmurze jest doskonała do tworzenia i testowania w chmurze. Można szybko utworzyć lub Zatrzymaj środowisko, w zależności od potrzeb.

- **Skalowalność w małych i średnich musi**: W scenariuszach, w których możesz potrzebować kilka maszyn wirtualnych w środowisku produkcyjnym zarządzanie niewielką liczbę maszyn wirtualnych może być przystępne cenowo, dopóki nie można przenieść do bardziej zaawansowanych środowisk PaaS, takich jak koordynatorów.

- **Środowiska produkcyjnego z istniejącymi narzędziami wdrażania**: Użytkownik może będziemy przenosić ze środowiska lokalnego, w którym zainwestowali w menu Narzędzia, aby złożonych wdrożeń maszyn wirtualnych i serwerów bez systemu operacyjnego (takich jak Puppet lub podobnego narzędzia). Aby przenieść do chmury przy minimalnych zmianach do procedur wdrażania środowiska produkcyjnego, można nadal używać tych narzędzi do wdrażania na maszynach wirtualnych platformy Azure. Jednak będziesz chciał użyć kontenery Windows jednostką wdrażania, aby poprawić środowisko wdrażania.

>[!div class="step-by-step"]
>[Poprzednie](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[dalej](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)