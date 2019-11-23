---
title: Kiedy należy wdrażać kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Kiedy należy wdrażać kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS Cloud)
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676899"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Kiedy należy wdrażać kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)

Jeśli Twoja organizacja korzysta z maszyn wirtualnych platformy Azure, nawet jeśli korzystasz również z kontenerów systemu Windows, nadal będziesz mieć IaaS. Oznacza to, że w przypadku działania infrastruktury, poprawek systemu operacyjnego maszyny wirtualnej i złożoności infrastruktury dla wysoce skalowalnych aplikacji należy wdrożyć na wielu maszynach wirtualnych w infrastrukturze o zrównoważonym obciążeniu. Główne scenariusze korzystania z kontenerów systemu Windows na maszynie wirtualnej platformy Azure to:

- **Środowisko deweloperskie/testowe**: maszyna wirtualna w chmurze doskonale nadaje się do programowania i testowania w chmurze. Możesz szybko utworzyć lub zatrzymać środowisko w zależności od potrzeb.

- **Wymagania dotyczące małych i średnich skalowalności**: w scenariuszach, w których może być potrzebne tylko kilka maszyn wirtualnych w środowisku produkcyjnym, zarządzanie niewielką liczbą maszyn wirtualnych może być przystępne do momentu przejścia do bardziej zaawansowanych środowisk PaaS, takich jak program Orchestrator.

- **Środowisko produkcyjne z istniejącymi narzędziami wdrażania**: możesz przejść ze środowiska lokalnego, w którym zainwestowano w narzędzia do tworzenia złożonych wdrożeń na maszynach wirtualnych lub serwerach bez systemu operacyjnego (takich jak Puppet lub podobne narzędzia). Aby przejść do chmury z minimalnymi zmianami w procedurach wdrażania w środowisku produkcyjnym, można nadal używać tych narzędzi do wdrażania na maszynach wirtualnych platformy Azure. Należy jednak użyć kontenerów systemu Windows jako jednostki wdrożenia, aby poprawić środowisko wdrażania.

>[!div class="step-by-step"]
>[Poprzedni](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[Następny](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
