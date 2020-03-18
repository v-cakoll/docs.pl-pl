---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503888"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach

Jak zauważono po przeczytaniu poprzednich sekcji, platforma Azure jest otwarta chmura, która oferuje wiele opcji. Możesz użyć najlepszego dopasowania do swoich potrzeb, jednak pojawia się również pytania o to, jakiego produktu / technologii należy użyć do swoich konteneryzowanych aplikacji.

Jako zalecenie *domyślne,* następujące kryteria są głównymi kryteriami zalecanymi w niniejszych wytycznych:

- **Pojedyncza monolityczna aplikacja:** Wybierz usługę aplikacji platformy Azure
- **Aplikacja N-Warstwowa:** Wybieranie koordynatorów, takich jak usługa Azure Kubernetes Service (AKS) lub usługa app service, jeśli masz jedną lub kilka usług zaplecza
- **Mikrousługi:** Wybierz aks lub aplikacje sieci Web platformy Azure dla kontenerów
- **Funkcje bezużycia serwera & programy obsługi zdarzeń:** Wybierz funkcje platformy Azure
- **Partia na dużą skalę:** Wybierz pozycję Azure Batch

Jednak zalecenie to należy przyjmować ze szczyptą soli, ponieważ wybór produktu zależy od potrzeb i cech konkretnego zastosowania. Nie wszystkie aplikacje są takie same, nawet jeśli początkowo mogą wyglądać podobne typy.

Po głębszej analizie potrzeb aplikacji wybrany produkt może być inny. Ale jako punkt wyjścia dobrze jest mieć wstępne wskazówki, z których można rozpocząć ocenę i testowanie na podstawie pewnego priorytetu.

W poniższej tabeli można zobaczyć podział różnych rodzajów aplikacji i ich możliwych i zalecanych scenariuszy hostingu platformy Azure.

| Architektura aplikacji | Maszyny wirtualne — maszyny wirtualne platformy Azure | ACI — wystąpienia kontenera platformy Azure | Usługa Azure App Service (kontenery w/w/o) | AKS — usługi Azure Kubernetes | Azure Functions | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Aplikacje internetowe (monolityczne)**         | ![Możliwe dzięki maszynom wirtualnym](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w usłudze app service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Możliwe dzięki AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **Aplikacje n-warstwowe (usługi)**        | ![Możliwe dzięki maszynom wirtualnym](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w usłudze app service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Możliwe dzięki AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki platformie Azure Fuctions](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Natywna w chmurze (mikrousługi)**  | | ![Możliwe dzięki ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Zalecane z AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Kontenery Linux)&nbsp;| ![Zalecane w usłudze Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Zdarzenie&#x2011;napędzane) | |
| **Zadania wsadowe/zadania (zadania w tle)** | ![Możliwe dzięki maszynom wirtualnym](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki usłudze app service](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w usłudze Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Zadania&nbsp;w tle) | ![Zalecane w usłudze Azure Batch](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Duża skala&#x2011;) |

**Legendy**

![Ikona Polecana](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Zalecane \
![Możliwa ikona](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Możliwe

> [!div class="step-by-step"]
> [Poprzedni](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [następny](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
