---
title: Kiedy należy wdrażać kontenery Windows w usłudze Azure Container Service (czyli Kubernetes)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kiedy należy wdrażać kontenery Windows w usłudze Azure Container Service (czyli Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 921767b52f2b0d80f2d31d972b65ac7551d2f7c5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643572"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Kiedy należy wdrażać kontenery Windows w usłudze Azure Container Service (czyli Kubernetes)

Usługa Azure Container Service optymalizuje konfigurację popularnych narzędzi typu open source i technologii pod kątem platformy Azure. Uzyskujesz otwarte rozwiązanie, przenośność kontenerów i konfiguracji aplikacji. Wybierasz rozmiar, liczbę hostów i narzędzia koordynatora. Usługa Azure Container Service obsługuje infrastrukturę dla Ciebie.

Jeśli pracujesz już z orkiestratorów typu open source, takich jak Kubernetes, Docker Swarm lub DC/OS, nie trzeba zmieniać swoje istniejących praktyk dotyczących zarządzania, aby przenieść obciążenia kontenerów do chmury. Użyj narzędzi do zarządzania aplikacjami, które już znasz z i połączyć za pośrednictwem standardowych punktów końcowych interfejsu API dla wybranego koordynatora.

Wszystkie te koordynatorów są dojrzałe środowiska, jeśli korzystają z kontenerów platformy Docker w systemie Linux, ale może składać się wyłącznie w wersji zapoznawczej dla kontenerów Windows.

Na przykład w usłudze Kubernetes, obsługa kontenerów jest natywne ("pełnoprawnym najwyższej jakości"), za pomocą kontenerów Windows na platformie Kubernetes jest również skutecznie (wersja zapoznawcza usługi ACS, począwszy od początku 2018 roku).

Ważna Uwaga: Wydzielonego i "więcej PaaS" (usługi Azure Kubernetes Service) w usłudze AKS jest wersja usługi ACS (Azure Container Service) dla rozwiązania Kubernetes, jednak Windows kontenery nie są nadal obsługiwane począwszy od 2 kwartale 2018 roku, ale obsługa zostanie dodana wkrótce.

>[!div class="step-by-step"]
>[Poprzednie](when-to-deploy-windows-containers-to-service-fabric.md)
>[dalej](choosing-azure-compute-options-for-container-based-applications.md)
