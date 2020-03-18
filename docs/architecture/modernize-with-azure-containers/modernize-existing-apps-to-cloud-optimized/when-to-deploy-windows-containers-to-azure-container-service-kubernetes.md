---
title: Kiedy wdrażać kontenery systemu Windows w usłudze Azure Container Service (czyli Kubernetes)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrażać kontenery systemu Windows w usłudze Azure Container Service (czyli Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676911"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Kiedy wdrażać kontenery systemu Windows w usłudze Azure Container Service (czyli Kubernetes)

Usługa Azure Container Service optymalizuje konfigurację popularnych narzędzi i technologii typu open source specjalnie dla platformy Azure. Otrzymujesz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia koordynatora. Usługa Azure Container Service obsługuje infrastrukturę dla Ciebie.

Jeśli pracujesz już z koordynatorami open source, takimi jak Kubernetes, Docker Swarm lub DC/OS, nie musisz zmieniać istniejących praktyk zarządzania, aby przenieść obciążenia kontenerów do chmury. Użyj narzędzi do zarządzania aplikacjami, które już znasz i połączyć się za pomocą standardowych punktów końcowych interfejsu API dla wybranego koordynatora.

Wszystkie te koordynatory są środowisk dojrzałych, jeśli używasz kontenerów platformy Docker systemu Linux, ale może być tylko w stanie podglądu dla kontenerów systemu Windows.

Na przykład w programie Kubernetes obsługa kontenerów jest natywna (obywatel pierwszej klasy), więc korzystanie z kontenerów systemu Windows w programie Kubernetes jest również skuteczne (w wersji zapoznawczej w programie ACS od początku 2018 r.).

Ważna uwaga: Ewoluowała i "więcej PaaS" wersja ACS (Usługa Azure Container Service) dla Kubernetes jest AKS (Usługa Azure Kubernetes), jednak kontenery systemu Windows nadal nie są obsługiwane od Q2 2018, ale będzie obsługiwana wkrótce.

>[!div class="step-by-step"]
>[Poprzedni](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[następny](choosing-azure-compute-options-for-container-based-applications.md)
