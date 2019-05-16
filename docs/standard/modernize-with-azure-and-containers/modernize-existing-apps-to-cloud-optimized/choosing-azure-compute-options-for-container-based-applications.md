---
title: Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach
ms.date: 05/04/2018
ms.openlocfilehash: 28e103c67f47d63582384c9ab468a5f631b5ce9e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638976"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Wybieranie platform obliczeniowych platformy Azure dla aplikacji opartych na kontenerach

Jak zauważono, należy po przeczytaniu w poprzednich sekcjach, platforma Azure jest Otwórz chmury, która oferuje wiele opcji do wyboru. Można użyć optymalnego dopasowania do własnych potrzeb, jednak również prezentuje pytania o jakie produktu/technologii, należy używać w przypadku aplikacji konteneryzowanych.

Jako *domyślnie* zalecenia, poniżej przedstawiono główne kryteria, zaleca się w tych wskazówkach:

- **Pojedynczy monolityczną aplikację:** Wybierz usługi Azure App Service
- **Aplikacja N-warstwowa:** Wybierz koordynatorów, takich jak Azure Kubernetes Service (AKS), Usługa Service Fabric (CPP) lub usługi App Service, jeśli masz jeden lub kilka usług zaplecza
- **Mikrousługi systemu Linux:** Wybierz usługi AKS/Kubernetes
- **Mikrousługi Windows:** Choose Service Fabric
- **Funkcje bezserwerowe & procedury obsługi zdarzeń:** Wybierz usługę Azure Functions
- **Na dużą skalę usługi Batch:** Wybierz usługi Azure Batch

Jednak to zalecenie powinna zostać podjęta uszczypnięcia soli, jak wybór produktu będzie zależeć od określonej aplikacji potrzebom i właściwości. Nie wszystkie aplikacje są takie same, nawet wtedy, gdy początkowo może wyglądać podobnych typów.

Po dogłębną analizę aplikacji potrzebom produktu wybrane mogą być inne. Jednak jako punktu wyjścia, warto mieć początkową pomoc, z których można uruchomić oceny i testowania na podstawie niektórych priorytetu.

Na poniższej ilustracji można analizować bardziej globalnego podczas tabeli szczegółowych decyzji.

![](./media/image8.5.png)

Zwróć uwagę sposób, w jaki bazowego systemu operacyjnego (Windows vs. System Linux) można także współczynnik decyzji, zgodnie z niektórych koordynatorów są bardziej dojrzała na kontenery systemu Linux i innych kontenerów Windows. Na przykład kontenery systemu Linux są bardzo dla dorosłych w usłudze Kubernetes (AKS na platformie Azure) ale mniej dojrzałe w usłudze Service Fabric. Z drugiej strony kontenery Windows są bardziej dojrzałych w usłudze Service Fabric (wydany w maja 2017 r.) i mniej dojrzałe w usłudze AKS.

Jednak te różnice w dojrzałości system operacyjny będzie w przyszłości zanikanie i wiele platform będą mieć porównywalne dojrzałości systemu operacyjnego i decyzji będzie określić więcej informacji na temat Preferencje na podstawie konkretnych cech, aplikacja może być konieczne lub oparte na każdej z platform ekosystem przyczyny.

> [!div class="step-by-step"]
> [Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
