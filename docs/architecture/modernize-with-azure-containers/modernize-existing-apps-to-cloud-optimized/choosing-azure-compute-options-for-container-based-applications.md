---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503888"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach

Ponieważ zauważysz, że po przeczytaniu poprzednich sekcji platforma Azure to otwarta chmura oferująca wiele opcji. Możesz jednak użyć najlepiej dopasowanej do Twoich potrzeb, a także zadać pytania dotyczące rodzaju produktu/technologii, które powinny być używane dla aplikacji w kontenerze.

Zgodnie z zaleceniami *domyślnymi* , poniżej przedstawiono główne kryteria zalecane w niniejszych wskazówkach:

- **Jednolite aplikacje:** Wybierz Azure App Service
- **Aplikacja N-warstwowa:** Wybierz usługi Orchestrator, takie jak Azure Kubernetes Service (AKS) lub App Service, jeśli masz jedną lub kilka usług zaplecza
- **Mikrousługi:** Wybierz AKS lub Web Apps platformy Azure dla kontenerów
- **Funkcje Bezserwerowe & obsługi zdarzeń:** Wybierz Azure Functions
- **Partia o dużej skali:** Wybierz Azure Batch

Jednakże to zalecenie powinno być podjęte z szczypania soli, ponieważ wybór produktu będzie zależeć od potrzeb i cech określonych aplikacji. Nie wszystkie aplikacje są takie same, nawet gdy początkowo mogą wyglądać podobnie.

Po dokładniejszej analizie potrzeb aplikacji wybrany produkt może być inny. Jednak jako punkt początkowy warto uzyskać wstępne wskazówki, w których można rozpocząć ocenianie i testowanie w oparciu o określony priorytet.

W poniższej tabeli przedstawiono podział różnych rodzajów aplikacji oraz ich możliwe i zalecane scenariusze hostingu platformy Azure.

| Architektura aplikacji | Maszyny wirtualne — Virtual Machines platformy Azure | ACI — Azure Container Instances | Azure App Service (w-m/wy) | AKS — usługa Azure Kubernetes Services | Azure Functions | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Aplikacje sieci Web (monolityczne)**         | ![Możliwe z maszynami wirtualnymi](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe z ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w przypadku App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Możliwe z AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **Aplikacje N-warstwowe (usługi)**        | ![Możliwe z maszynami wirtualnymi](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe z ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w przypadku App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Możliwe z AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe za pomocą usługi Azure fuctions](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Chmura — natywne (mikrousługi)**  | | ![Możliwe z ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Zalecane z AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (&nbsp;kontenery systemu Linux)| ![Zalecane w przypadku Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Sterowane zdarzeniami&#x2011;) | |
| **Partia/zadania (zadania w tle)** | ![Możliwe z maszynami wirtualnymi](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe z ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe z App Service](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Możliwe z AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Zalecane w przypadku Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Zadania&nbsp;w tle) | ![Zalecane w przypadku Azure Batch](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Duża&#x2011;skala) |

**Legendy**

![Zalecana ikona](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Rekomendowane
![Możliwa ikona](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Najmniejszy

> [!div class="step-by-step"]
> [Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
