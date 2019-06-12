---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833854"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach

Jak zauważono, należy po przeczytaniu w poprzednich sekcjach, platforma Azure jest Otwórz chmury, która oferuje wiele opcji do wyboru. Można użyć optymalnego dopasowania do własnych potrzeb, jednak również prezentuje pytania o jakie produktu/technologii, należy używać w przypadku aplikacji konteneryzowanych.

Jako *domyślnie* zalecenia, poniżej przedstawiono główne kryteria, zaleca się w tych wskazówkach:

- **Pojedynczy monolityczną aplikację:** Wybierz usługi Azure App Service
- **Aplikacja N-warstwowa:** Wybierz koordynatorów, takich jak Azure Kubernetes Service (AKS) lub usługi App Service, jeśli masz jeden lub kilka usług zaplecza
- **Mikrousługi:** Wybierz usługi AKS lub usługi Azure Web Apps for Containers
- **Funkcje bezserwerowe & procedury obsługi zdarzeń:** Wybierz usługę Azure Functions
- **Na dużą skalę usługi Batch:** Wybierz usługi Azure Batch

Jednak to zalecenie powinna zostać podjęta uszczypnięcia soli, jak wybór produktu będzie zależeć od określonej aplikacji potrzebom i właściwości. Nie wszystkie aplikacje są takie same, nawet wtedy, gdy początkowo może wyglądać podobnych typów.

Po dogłębną analizę aplikacji potrzebom produktu wybrane mogą być inne. Jednak jako punktu wyjścia, warto mieć początkową pomoc, z których można uruchomić oceny i testowania na podstawie niektórych priorytetu.

Na poniższej ilustracji widać podział różnych rodzajów aplikacji i ich idealne rozwiązanie Azure w scenariuszach hostingu.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
