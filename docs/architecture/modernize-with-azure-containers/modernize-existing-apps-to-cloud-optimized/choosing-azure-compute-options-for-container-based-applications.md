---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 02/18/2020
ms.openlocfilehash: 4bc72fb5a5be30d47cffe73d53a82b3237a959a6
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987819"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach

Jak zauważyłeś po przeczytaniu poprzednich sekcji, platforma Azure jest otwartą chmurą, która oferuje wiele możliwości wyboru. Można użyć najlepszego dopasowania do swoich potrzeb, jednak również powierzchnie pytania o produkt / technologii należy użyć do aplikacji konteneryzowanych.

Jako *domyślne* zalecenie, główne kryteria zalecane w niniejszych wytycznych:

- **Pojedyncza monolityczna aplikacja:** Wybieranie usługi aplikacji platformy Azure
- **Aplikacja N-Tier:** Wybierz koordynatorów, takich jak Usługa Azure Kubernetes Service (AKS) lub App Service, jeśli masz jedną lub kilka usług zaplecza
- **Mikrousługi:** Wybieranie usługi AKS lub usługi Azure Web Apps dla kontenerów
- **Funkcje bezserwerowe & programy obsługi zdarzeń:** Wybieranie funkcji platformy Azure
- **Partia na dużą skalę:** Wybierz usługę Azure Batch

Jednak to zalecenie należy przyjmować ze szczyptą soli, ponieważ wybór produktu będzie zależeć od potrzeb i cech konkretnego zastosowania. Nie wszystkie aplikacje są takie same, nawet jeśli początkowo mogą wyglądać podobne typy.

Po głębszej analizie potrzeb aplikacji wybrany produkt może być inny. Ale, jako punkt wyjścia, dobrze jest mieć wstępne wskazówki, od których można rozpocząć ocenę i testowanie na podstawie pewnego priorytetu.

W poniższej tabeli można zobaczyć podział różnych rodzajów aplikacji i ich możliwych i zalecanych scenariuszy hostingu platformy Azure.

| Architektura aplikacji | Maszyny wirtualne — maszyny wirtualne platformy Azure | ACI — wystąpienia kontenera platformy Azure | Usługa Azure App Service (kontenery typu w-bez/o) | AKS — usługi Azure Kubernetes | Azure Functions | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Aplikacje sieci Web (monolityczne)**         | ![Możliwe z maszynami wirtualnymi](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe z ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w usłudze app service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Możliwe dzięki AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **Aplikacje warstwy N (usługi)**        | ![Możliwe z maszynami wirtualnymi](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe z ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w usłudze app service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Możliwe dzięki AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki usłudze Azure Fuctions](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Natywne dla chmury (mikrousługi)**  | | ![Możliwe z ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Zalecane z AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Kontenery Linuksa)&nbsp;| ![Zalecane w usłudze Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Zdarzenie&#x2011;sterowane) | |
| **Zadania wsadowe/wytłmowe (zadania w tle)** | ![Możliwe z maszynami wirtualnymi](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe z ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki usłudze app service](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe dzięki AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w usłudze Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Zadania&nbsp;w tle) | ![Zalecane w przypadku usługi Azure Batch](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Duża skala&#x2011;) |

**Legendy**

![Zalecana ikona](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Zalecane \
![Możliwa ikona](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Możliwe

> [!div class="step-by-step"]
> [Poprzedni](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [następny](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
