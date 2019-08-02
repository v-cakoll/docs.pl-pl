---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68677037"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach

Ponieważ zauważysz, że po przeczytaniu poprzednich sekcji platforma Azure to otwarta chmura oferująca wiele opcji. Możesz jednak użyć najlepiej dopasowanej do Twoich potrzeb, a także zadać pytania dotyczące rodzaju produktu/technologii, które powinny być używane dla aplikacji w kontenerze.

Zgodnie z zaleceniami domyślnymi, poniżej przedstawiono główne kryteria zalecane w niniejszych wskazówkach:

- **Jednolite aplikacje:** Wybierz Azure App Service
- **Aplikacja N-warstwowa:** Wybierz usługi Orchestrator, takie jak Azure Kubernetes Service (AKS) lub App Service, jeśli masz jedną lub kilka usług zaplecza
- **Mikrousług** Wybierz AKS lub Web Apps platformy Azure dla kontenerów
- **Funkcje bezserwerowe & obsługi zdarzeń:** Wybierz Azure Functions
- **Partia o dużej skali:** Wybierz Azure Batch

Jednakże to zalecenie powinno być podjęte z szczypania soli, ponieważ wybór produktu będzie zależeć od potrzeb i cech określonych aplikacji. Nie wszystkie aplikacje są takie same, nawet gdy początkowo mogą wyglądać podobnie.

Po dokładniejszej analizie potrzeb aplikacji wybrany produkt może być inny. Jednak jako punkt początkowy warto uzyskać wstępne wskazówki, w których można rozpocząć ocenianie i testowanie w oparciu o określony priorytet.

Na następnym rysunku można zobaczyć podział różnych rodzajów aplikacji i ich idealne scenariusze hostingu platformy Azure.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Poprzedni](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)Następny
> [](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
