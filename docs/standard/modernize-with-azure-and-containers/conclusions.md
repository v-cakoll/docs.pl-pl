---
title: Wnioski
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów Windows | wnioski
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: af6151d04622c72acdb7f27ebb220bf611418b4c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743972"
---
# <a name="conclusions"></a>Wnioski

- Rozwiązania oparte na kontenerach ostatecznie zapewniają korzyści oszczędności kosztów. Kontenery są rozwiązania problemów z wdrażaniem, ponieważ usuwają zajmowania się przyczyną braku zależności w środowiskach produkcyjnych. Przez usunięcie tych problemów, jego znacznie poprawia operacje tworzenia i testowania, metodyki DevOps i produkcyjnych.

- Kontener platformy Docker, staje się standardową jednostką wdrożenia dla dowolnej usługi lub aplikacji opartej na serwerze.

- W środowiskach produkcyjnych należy użyć koordynatora (np. usługi Service Fabric lub Kubernetes) do hostowania aplikacji dla komputerów z systemem Windows kontenery skalowalne.

- Maszyny wirtualne platformy Azure, hostingu kontenerów to szybki i prosty sposób tworzenia małych środowiska deweloperskie i testowe w chmurze.

- Wystąpienie usługi Azure SQL Database Managed zaleca się domyślnie, migrując relacyjnych baz danych z istniejących aplikacji na platformie Azure.

- Visual Studio 2017 i Image2Docker są podstawowych narzędzi do uruchamiania modernizowanie istniejących aplikacji .NET za pomocą kontenerów Windows, przyspieszając pobierania wprowadzenie nauki.

- W przypadku umieszczenia konteneryzowanych aplikacji w środowisku produkcyjnym będzie zawsze utworzyć lub przyjęcie kultury DevOps i narzędzi DevOps dla potoków ciągłej integracji/ciągłego Dostarczania, takich jak usługom DevOps platformy Azure lub usługi Jenkins.

- Microsoft Azure oferuje najbardziej kompleksowy i kompletne środowisko do modernizacji istniejących aplikacji .NET Framework z kontenerami Windows, infrastruktury chmury i usług PaaS.

>[!div class="step-by-step"]
[Poprzednie](walkthroughs-technical-get-started-overview.md)