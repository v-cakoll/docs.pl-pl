---
title: Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958291"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)

Usługa kontenera platformy Azure optymalizuje konfiguracji popularnych open source narzędzia i technologie specjalnie dla platformy Azure. Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność zarówno w przypadku kontenerów, jak i konfigurację aplikacji. Należy wybrać rozmiar, liczby hostów i narzędzia programu orchestrator. Usługa kontenera platformy Azure obsługuje infrastrukturę dla Ciebie.

Jeśli korzystasz już z orchestrators open source, takie jak Kubernetes, DC/OS lub Docker Swarm, nie musisz zmienić swoje istniejące praktyki zarządzania przenoszenie kontenera obciążeń do chmury. Użyj narzędzia do zarządzania aplikacjami, które znasz już i połączenia za pomocą standardowych punktów końcowych interfejsu API programu orchestrator wybranych przez użytkownika.

Wszystkie te orchestrators są dojrzałe środowisk, jeśli używasz kontenery Linux Docker, ale tylko może być w stanie Podgląd kontenery systemu Windows.

Na przykład w Kubernetes, obsługa kontenerów jest native (najwyższej jakości obywateli), za pomocą kontenery systemu Windows na Kubernetes obowiązuje również (w wersji zapoznawczej usługi ACS od początku 2018).

Ważna Uwaga: wydzielonego i "więcej PaaS" wersja ACS (usługi kontenera platformy Azure) dla Kubernetes jest AKS (usługa Azure Kubernetes), jednak kontenery systemu Windows nie są nadal obsługiwane począwszy od 2018 K2, ale będzie możliwe wkrótce.

>[!div class="step-by-step"]
[Poprzednie](when-to-deploy-windows-containers-to-service-fabric.md)
[dalej](choosing-azure-compute-options-for-container-based-applications.md)
