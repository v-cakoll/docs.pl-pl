---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 05/04/2018
ms.openlocfilehash: 079c9c5ca02b6dc75214d63cb59afdead03d3190
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "73736998"
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

Na rysunku 1 można zobaczyć podział różnych rodzajów aplikacji i ich idealne scenariusze hostingu platformy Azure.

![Tabela, w której scenariusze hostingu platformy Azure są najlepsze dla różnych aplikacji.](./media/choosing-azure-compute-options-for-container-based-applications/azure-hosting-scenarios-for-apps.png)

> [!div class="step-by-step"]
> [Poprzedni](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Następny](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
