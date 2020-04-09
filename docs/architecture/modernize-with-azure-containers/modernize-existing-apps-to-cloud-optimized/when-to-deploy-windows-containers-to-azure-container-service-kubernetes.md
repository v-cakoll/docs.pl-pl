---
title: Kiedy wdrożyć kontenery systemu Windows w usłudze kontenerów platformy Azure (czyli w usłudze Kubernetes)
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrożyć kontenery systemu Windows w usłudze kontenerów platformy Azure (czyli w usłudze Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 3ff51a70d4e158b831155ab4992ec32f5d98cedb
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987767"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Kiedy wdrożyć kontenery systemu Windows w usłudze kontenerów platformy Azure (czyli w usłudze Kubernetes)

Usługa Azure Container Service optymalizuje konfigurację popularnych narzędzi i technologii typu open source specjalnie dla platformy Azure. Otrzymujesz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i dla konfiguracji aplikacji. Można wybrać rozmiar, liczbę hostów i narzędzia aranżatora. Usługa Azure Container Service obsługuje infrastrukturę za Ciebie.

Jeśli już pracujesz z koordynatorami open source, takimi jak Kubernetes, Docker Swarm lub DC/OS, nie musisz zmieniać istniejących praktyk zarządzania, aby przenieść obciążenia kontenerów do chmury. Użyj narzędzi do zarządzania aplikacjami, które są już znane i połączyć za pośrednictwem standardowych punktów końcowych interfejsu API dla koordynatora do wyboru.

Wszystkie te orchestrators są środowiskami dojrzałymi, jeśli używasz kontenerów platformy Docker systemu Linux, ale może być tylko w stanie podglądu dla kontenerów systemu Windows.

Na przykład w usłudze Kubernetes obsługa kontenerów jest natywna (obywatel pierwszej klasy), więc używanie kontenerów systemu Windows w usłudze Kubernetes jest również skuteczne (w wersji zapoznawczej w programie ACS na początku 2018 r.).

Ważna uwaga: Ewoluowała i "więcej PaaS" wersja usługi ACS (Usługa azure kontenera) dla usługi Kubernetes jest AKS (Usługa Azure Kubernetes), jednak kontenery systemu Windows nadal nie są obsługiwane od Q2 2018, ale wkrótce będą obsługiwane.

>[!div class="step-by-step"]
>[Poprzedni](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[następny](choosing-azure-compute-options-for-container-based-applications.md)
