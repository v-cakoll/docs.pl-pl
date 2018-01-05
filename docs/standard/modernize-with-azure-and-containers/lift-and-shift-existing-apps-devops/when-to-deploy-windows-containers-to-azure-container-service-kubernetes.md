---
title: "Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f7ed0c9ebf1c80ae6cae4311b2682d3cc161623
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Kiedy należy wdrożyć kontenery systemu Windows dla usługi kontenera platformy Azure (czyli Kubernetes)

Usługa kontenera platformy Azure optymalizuje konfiguracji popularnych open source narzędzia i technologie specjalnie dla platformy Azure. Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność zarówno w przypadku kontenerów, jak i konfigurację aplikacji. Należy wybrać rozmiar, liczby hostów i narzędzia programu orchestrator. Usługa kontenera platformy Azure obsługuje infrastrukturę dla Ciebie.

Jeśli korzystasz już z orchestrators open source, takie jak Kubernetes, DC/OS lub Docker Swarm, nie musisz zmienić swoje istniejące praktyki zarządzania przenoszenie kontenera obciążeń do chmury. Użyj narzędzi zarządzania aplikacji jest już znanych i połączenia za pomocą standardowych punktów końcowych interfejsu API programu orchestrator wybranych przez użytkownika.

Wszystkie te orchestrators są dojrzałe środowisk, jeśli używasz kontenery Linux Docker, ale one również obsługę kontenery systemu Windows zgodnie z 2017 (część wcześniej, część niedawno, w zależności od orchestrator).

Na przykład w Kubernetes, obsługa kontenerów jest native (najwyższej jakości obywateli), za pomocą kontenery systemu Windows na Kubernetes jest również bardzo wydajny i niezawodny (w wersji zapoznawczej do wcześniej dzielą 2017).

>[!div class="step-by-step"]
[Poprzednie](when-to-deploy-windows-containers-to-service-fabric.md)
[dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
