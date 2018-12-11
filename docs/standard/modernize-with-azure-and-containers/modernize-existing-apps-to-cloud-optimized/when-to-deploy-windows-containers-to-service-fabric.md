---
title: Kiedy należy wdrażać kontenery Windows do usługi Service Fabric
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kiedy należy wdrażać kontenery Windows do usługi Service Fabric
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 01d76f325480c7cf09fef36b02589a602e3ee11e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129509"
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Kiedy należy wdrażać kontenery Windows do usługi Service Fabric

Aplikacje, które są oparte na Windows kontenery szybko będą musieli używać platformy, które jeszcze bardziej przemieścić się z maszyn wirtualnych IaaS. Są to zwiększona skalowalność zautomatyzowane i wysokiej skalowalności i uzyskać znaczne ulepszenia w środowisku pełnego zarządzania, w przypadku wdrożeń uaktualnienia, przechowywanie wersji, wycofywanie zmian oraz monitorowanie kondycji. Tych celów można osiągnąć za pomocą programu orchestrator w usłudze Azure Service Fabric dostępnych w chmurze Microsoft Azure, ale również w środowisku lokalnym lub nawet w innej chmurze.

W wielu organizacjach są podnoszenia i przesunięcie istniejące aplikacje monolityczne do kontenerów dwóch powodów:

-   Obniżenie kosztów, albo z powodu konsolidacji i usuwania istniejącego sprzętu lub uruchamianie aplikacji na zwiększenie gęstości.

-   Kontrakt spójne wdrażanie, między środowiskami deweloperskim i operacji.

Należy wykonać redukcję kosztów jest zrozumiałe i jest prawdopodobne, że posiadać wszystkie organizacje są łączone w celu. Spójne wdrażanie jest trudniejsze do oceny, ale jest równie jako ważne. Kontrakt spójne wdrażanie mówi, że deweloperzy mogą skorzystać z technologii, która odpowiada ich, a zespół operacyjny pobiera jeden sposób wdrażać aplikacje oraz zarządzać nimi. Niniejsza Umowa uwalnia posiadające operacje przeciwdziałania złożoność wielu różnych technologii lub wymuszanie deweloperom pracę tylko w przypadku niektórych technologii. Zasadniczo każda aplikacja jest konteneryzowana w obrazie niezależna wdrożenia.

Niektóre organizacje będą nadal modernizacji przez dodanie mikrousługi (aplikacjom natywnym dla chmury), ale inne organizacje będą zatrzymać w tym miejscu (aplikacje zoptymalizowane pod kątem chmury). Jak pokazano w rysunek 4 – 8, organizacje te nie będą przenieść do architektury mikrousług, ponieważ nie może być konieczne. W każdym przypadku już otrzymują korzyści, za pomocą kontenerów, a także usługi Service Fabric a zapewnia wszystkie funkcje zarządzania obejmującą wdrożenia uaktualnień, przechowywanie wersji, wycofywania i monitorowanie kondycji.

> ![Lift- and -shift aplikacji usługi Service Fabric](./media/image8.png)
>
> **Rysunek 4 – 8.** Lift- and -shift aplikacji usługi Service Fabric

To podejście klucza do usługi Service Fabric jest ponowne używanie istniejącego kodu i lift and shift. W związku z tym można przeprowadzić migrację istniejących aplikacji .NET Framework, przy użyciu kontenerów Windows i wdrożyć je do usługi Service Fabric. Będzie łatwiejszy do zachowania, przechodząc modernizowanie, po pewnym czasie, dodając nowe mikrousługi.

Porównując usługi Service Fabric do innych orkiestratorów, jest ważne podkreślić, że Usługa Service Fabric to dojrzała na uruchamianie aplikacji systemu Windows i usługi. Usługa Service Fabric jest uruchomiony usług opartych na Windows i aplikacji, w tym warstwy 1 o krytycznym znaczeniu produktów firmy Microsoft przez lata. Była pierwszym orchestrator zapewnienie ogólnej dostępności dla kontenerów Windows. Inne kontenery, takich jak Kubernetes, DC/OS i Docker Swarm, są bardziej dojrzałych w systemie Linux, ale mniej dojrzałe niż aplikacje usługi Service Fabric dla Windows i Windows kontenery.

Jest ostatecznym celem usługi Service Fabric do zmniejszenia złożoności tworzenia aplikacji przy użyciu podejścia mikrousług. Po pewnym czasie ma mikrousług dla niektórych typów aplikacji, aby uniknąć kosztownych operacje przeprojektowania. Może na początku są małe, skalowania w razie, wycofaniu usługi, dodać nowe usługi i rozwój aplikacji przy użyciu klienta. Istnieje wiele problemów, które są jeszcze, które należy rozwiązać się mikrousług bardziej przystępne dla większości deweloperów. Jeśli aktualnie jesteś właśnie podnoszenia i przesunięcie aplikacji za pomocą kontenerów Windows, ale myślisz o dodawaniu mikrousług oparte na kontenerach w przyszłości, to miejsce, gdzie sweet usługi Service Fabric.

>[!div class="step-by-step"]
>[Poprzednie](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
>[dalej](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)