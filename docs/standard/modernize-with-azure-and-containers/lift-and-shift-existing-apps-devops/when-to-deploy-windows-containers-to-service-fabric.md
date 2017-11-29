---
title: "Podczas wdrażania systemu Windows kontenery sieci szkieletowej usług"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Podczas wdrażania systemu Windows kontenery sieci szkieletowej usług"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 21b6c348991e07dac7dbc9d327b63fa88a588ba4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Podczas wdrażania systemu Windows kontenery sieci szkieletowej usług

Aplikacje, które są oparte na Windows kontenery szybko będą musieli używać platformy, które jeszcze bardziej przemieścić z maszyn wirtualnych IaaS. Jest lepsze automatyczne skalowanie i Wysoka skalowalność i uzyskanie wprowadzono znaczne ulepszenia w środowisku pełnego zarządzania, w przypadku wdrożeń uaktualnienia, wersji, wycofywania i monitorowanie kondycji. Z programem orchestrator sieć szkieletowa usług Azure, dostępny w chmurze Microsoft Azure, ale również lokalnymi lub nawet w innej chmurze można osiągnięcie tych celów.

W wielu organizacjach są podnoszenia i przesunięcie istniejące aplikacje wbudowanymi do kontenerów dwóch powodów:

-   Obniżenie kosztów, albo z powodu konsolidacji i usunięcia istniejącego sprzętu lub uruchomienie aplikacji o wyższej gęstości.

-   Kontrakt spójne wdrażanie między rozwoju i operacji.

Realizacji redukcję kosztów jest zrozumiałe, a istnieje duże prawdopodobieństwo, że wszystkie organizacje są łączone ten cel. Spójne wdrażanie trudniej jest dokonanie oceny, ale jest równie jako ważne. Kontrakt spójne wdrażanie mówi, że deweloperzy mogą używać technologii pasujące do nich, a zespół operacyjny pobiera jeden sposób na wdrażanie aplikacji i zarządzanie nimi. Niniejsza Umowa wyeliminować słabe o operacji postępowania w przypadku złożoność wiele różnych technologii lub wymuszania deweloperom działa tylko w przypadku niektórych technologii. Zasadniczo każda aplikacja jest konteneryzowanych niezależne wdrożenia obrazu.

Niektóre organizacje będą nadal modernizacji przez dodanie mikrousług (zoptymalizowanych pod kątem chmury oraz chmury natywne aplikacje). W wielu organizacjach przestanie tutaj (gotowe DevOps chmury). Jak pokazano na rysunku 4-8, organizacje te nie będą przenieść do architektury mikrousług, ponieważ nie może być konieczne. W każdym przypadku już otrzymują korzyści, że przy użyciu kontenerów i sieci szkieletowej usług środowisko zawiera a pełnego zarządzania, które obejmuje wdrażanie, uaktualnia, wersji, wycofywania i monitorowanie kondycji.

> ![Podnieś i przesunięcia aplikacji sieci szkieletowej usług](./media/image8.png)
>
> **Rysunek 4-8.** Podnieś i przesunięcia aplikacji sieci szkieletowej usług

Klucza podejście do sieci szkieletowej usług jest ponownie wykorzystać istniejący kod i po prostu podnieś i przesunięcia. W związku z tym można migracji bieżącej aplikacji .NET Framework, za pomocą kontenery systemu Windows i wdrożyć je w sieci szkieletowej usług. Będzie łatwiejszy do zachowania, przechodząc modernizacji, po pewnym czasie, dodając nowe mikrousług.

Porównanie usług sieci szkieletowej do innych orchestrators, jest ważne wyróżnić się bardzo dojrzałe na uruchamianie aplikacji systemu Windows i usługi sieć szkieletowa usług. Usługi systemu Windows i aplikacji, w tym warstwy 1, krytycznym produktów firmy Microsoft, lat była uruchomiona sieci szkieletowej usług. Był pierwszy orchestrator ma ogólnej dostępności dla kontenerów systemu Windows (maj 2017). Inne kontenery, takie jak Kubernetes, DC/OS i Docker Swarm, są bardziej dojrzałe w systemie Linux, ale dojrzałe mniej niż aplikacji opartych na sieci szkieletowej usług dla systemu Windows i kontenery systemu Windows.

Ostatecznym celem usługi sieć szkieletowa jest zmniejszenie złożoności Kompilowanie aplikacji przy użyciu metody mikrousług. Jest to, gdzie ostatecznie mają być dla niektórych typów aplikacji, aby uniknąć kosztownych redesigns. Można rozpoczęcie od czegoś małego, skalowanie w razie potrzeby, zastąpić usług, dodawanie nowych usług i rozwijać aplikacji z użyciem klienta. Wiemy, że istnieje wiele problemów, które jeszcze mają zostać rozwiązane dokonać bardziej przystępne mikrousług większość deweloperów. Jeśli obecnie jest po prostu podnoszenia oraz zmieni aplikacji z kontenerami systemu Windows, ale myślisz o dodanie mikrousług oparte na kontenery w przyszłości, to miejsce słodka sieci szkieletowej usług.

>[!div class="step-by-step"]
[Poprzednie](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[dalej](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
